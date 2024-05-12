# Lost in Translation, a shaky crossing with ORM

![logo](../pix/viiinzzz48.png){: style="float: left"}
*Մι∩z•thedev* · [Follow](mailto:vinz.thedev@gmail.com)
Published in *Coding* · 6 min read · 1 day ago
___
<span style="font-size:2.5em">👏</span>65k <span style="font-size:2.5em">💬</span>321 <span style="font-size:2.5em">🔖</span> <span style="font-size:2.5em">⤴️</span>
___

![pix](../pix/orm-unicorn.webp)

# ORM

Objects are not Tabular Data. Nonetheless SQL is often wished for its relations and data integrity.
Hence ORM come into the game, they promise to bridge the gap between the two paradigms. A map is never perfect though...

On one hand a full fledge ORM like .Net Entity Framework (EF) may do too much, on the other hand a micro ORM like Dapper may not do enough. Yes EF can easily drain too much data, it's often a performance debacle, unless properly understood. Yes Dapper makes you write a lot of code and queries, it helps but it does not look very DRY. What is the adequate trade-off then ? I'd say, probably a relaxed EF.

What about tackling the problem at its source, Objects are not flat, so let's choose a document DB like Mongo, especially if we still need advanced computation, the Mongo DB engine will be happy to do it. In that case you just have to pay attention the business logic will slide into the queries and aggregate operations. In the case SQL is a requirement, DB like Postgres can store Json or Xml and query it very well but I don't think it can aggregate as cleverly as Mongo does. If a mix of structured and unstructured data, I would choose Postgres.

If you want EF as a query builder on steroid and be the master of object tracking, you can do CRUD like this :
```csharp

public int Create(Room room)
{
    var entity = _context.Rooms.Add(room);
    _context.SaveChanges();
    entity.State = EntityState.Detached;

    return room.RoomId;
}

public IQueryable<Room> Rooms(int hotelId)

     => _context.Rooms
         .AsNoTracking()
         .Where(room => room.HotelId == hotelId);
         
public Room? GetRoom(int roomId)
{
    var room = _context.Rooms
        .Find(roomId);

    if (room == default) return default;

    _context.Entry(room).State = EntityState.Detached;

    return room;
}
 
 public Room Update(int roomId, UpdateRoom update)
 {
     var room = _admin.Rooms
         .Find(roomId);

     if (room == default)
     {
         throw new InvalidOperationException("roomId not found");
     }

     _context.Entry(room).State = EntityState.Detached;

     room = room.Patch(update);//your patch method

     var entity = _admin.Rooms.Update(room);
     _context.SaveChanges();
     entity.State = EntityState.Detached;

     return room;
}
```

# Business logic location

Useful entities are not anemic they have business logic. Business logic is naturally expressed in C# statements which for simple operators 'might' get translated to appropriate SQL statements. It's fine for damn simple rules, however complex rules simply won't fit neither into an expression tree, nor to a LINQ to SQL. I found myself many times writing a C# rule looking clever and simple and EF complained it was not possible to map it, so I had to rework the logic and the data structure.

Why all this translation wanking? for performance of course. We can't afford bringing in all the rows all the times into the RAM to have the luxury to crunch the data with our favorite language. We need to have the DB do its part of the job. Sure primarily its role is to store ACIDly but it can and should manipulate (in-DB) as much as possible before the proper retrieval step.

Obviously when computed data can be pre-calculated and stored in advance, it's less a burden to query thereafter already-made material but sometimes computed data is expressed dynamically and needs calculation at query time. So we need to have that expression being flown right into the SQL engine. Can LINQ+EF do it ? it all depends. Some wizard 3rd-party libs might help, partially.

So one may end up with neither C#, neither SQL but some expression tree, that looks unsatisfactory, performs great, and that may be DRY, well it's like a centaur artefact, shall we be proud or shameful of it?

https://www.daveaglick.com/posts/computed-properties-and-entity-framework

# Computed Properties and Entity Framework

How to use your computed properties in predicates and projections.

```
public class Customer
{
  public string FirstName { get; set; }
  public string LastName { get; set; }
  public virtual ICollection<Holding> Holdings { get; private set; }

  [NotMapped]
  public decimal AccountValue
  {
    get { return Holdings.Sum(x => x.Value); }
  }
}

public class Holding
{
  public virtual Stock Stock { get; set; }
  public int Quantity { get; set; }

  [NotMapped]
  public decimal Value
  {
    get { return Quantity * Stock.Price; }
  }
}

public class Stock
{
  public string Symbol { get; set; }
  public decimal Price { get; set; }
}
```

The problems start when you want to use them within a query or as part of a projection. For example, the following query will throw an exception:

```
var customers = ctx.Customers.Where(c => c.AccountValue > 10);
```

Don't Use Computed Properties
Entity Framework does not know how to translate to SQL so a naive workaround for simple query is to translate ourselves however it repeat and spread out the business logic, so it's a no go

```
var customers = ctx.Customers.Where(c => c.Holdings.Sum(h => h.Quantity * h.Stock.Price) > 10);
```

Materializing entities with a ToList ToArray or AsEnumerable is neither recommended cause the client will filter, not the DB, hence draining all the data down.

Solution :
To reach the DRY goal, the business logic shall work on queryable so it can be reused
https://github.com/damieng/Linq.Translations

```csharp
partial class Employee {
    private static readonly CompiledExpression<Employee,string> fullNameExpression = 
      DefaultTranslationOf<Employee>.Property(e => e.FullName)
        .Is(e => e.Forename + " " + e.Surname);
    private static readonly CompiledExpression<Employee,int> ageExpression =
      DefaultTranslationOf<Employee>.Property(e => e.Age)
        .Is(e => DateTime.Now.Year - e.BirthDate.Value.Year - 
          (((DateTime.Now.Month < e.BirthDate.Value.Month) || 
          (DateTime.Now.Month == e.BirthDate.Value.Month && 
          DateTime.Now.Day < e.BirthDate.Value.Day)) ? 1 : 0)));

  public string FullName {
    get { return fullNameExpression.Evaluate(this); }
  }

  public int Age {
    get { return ageExpression.Evaluate(this); }
  }
}

var employees = db.Employees
                  .Where(e => e.FullName.Contains("da"))
                  .GroupBy(e => e.Age)
                  .WithTranslations();
```

However:
- An expression tree cannot contain switch expression `x switch { y => ...`
- An expression tree cannot contain throw expression `?? throw ...` though it could be a COALESCE
- An expression tree cannot contain conditional access operator `?.`
- It 'could' contain ternary `? :`  it ought to turn into a CASE WHEN
- It can contains subexpression nested computed
- DateTime conversion to TotalHours : no chance, keep TimeLapse
- ...
however plenty lot deceitful follows... that makes you think: mmh, time to break up me DRY promise n' head back to good ole sequel?

https://learn.microsoft.com/en-us/ef/core/providers/sqlite/functions#date-and-time-functions

## DateTime

DateTime.Now supposed to be translated but it is not
and on the top I should not trust the database has my correct time
indeed in my case it has not since I use a fake time in the business logic
so I thought I should add a 'middleware' to store my time update before each query and use that time reference for any indb time calc
does it sound comprehensible, does it even make sense ?

DateTime stored in DB by EF is almost useless for advanced calc. Better pre-store a float day number for example

```csharp
var priority = (RoomServiceDuty duty) =>
{
	var prevDays = Days(duty.FreeTime, now);
	var nextDays = Days(now, duty.BusyTime);
	return duty.FloorNum * (
		nextDays == 0 ? 100_000 //today high priority
		: nextDays == 1 ? 10_000 //tomorrow medium priority
		: (prevDays >= 9 ? 9 : prevDays) * 1_000 //then the more stink the more urgent
	);
};
```
