# C# Language Tips 4

![logo](../pix/viiinzzz48.png){: style="float: left"}
*Մι∩z•thedev* · [Follow](mailto:vinz.thedev@gmail.com)
Published in *Coding* · 6 min read · 1 day ago
___
<span style="font-size:2.5em">👏</span>65k <span style="font-size:2.5em">💬</span>321 <span style="font-size:2.5em">🔖</span> <span style="font-size:2.5em">⤴️</span>
___
## `catch`ing several fishes at once

```csharp
catch (Exception ex) when (ex is 
    AException or
    BException
) {

}
```

![pix](../pix/catchfish.webp)

## Spread `..`

You certainly know Javascript triple dot **spread** operator `...`
I found a rather close notation in C#, not as versatile but it's handy.

Imagine you need to **materialize** an IEnumerable (ie. actually perform the fetch, the calculation, or whatever job), you may call `myEnumerable.ToArray()`

In modern C# you may write `[..myEnumerable]` It looks much like js `[...array]`
Notice that C# spread is only double dot `..` / unlike js triple dot `...`

However type inference is not optimum and it may require additional forehead type specification.

![pix](../pix/spreaddigits.webp)

## `.AsParallel().WithCancellation(token)`

⚠ Beware **Parallel Linq** does not check cancellation at each iteration **but every 64**, 
apparently striving to preserve performance for short loops,
so it does incomb to the inner lambda to check upon cancellation each time **if deemed necessary.**

==> Overall that makes Parallel Linq **not so reliable for long async processes.**

## `global using`

It the module (the dll, the project) is well delimited/tailored, SRP compliant if you will, then its dependencies should be few, shared and **centralizable**.

For DRY purpose and matter of brevity,
I like factorizing maximum amount of `using` into the `GlobalUsings.cs
having the `global using libA;`
eventually `global using static helperB;`.

This way when reading a source file **we start straight to the point**, hence it is easier to catch up.

## `await using`

**Disposable** resources may perform _cleanup/teardown/dispose_.
_Call that final sequence the way you like_
- **asynchronously** as proposed in the `IAsyncDisposable` interface
rather than doing it
- **synchronously** like in the traditional `IDisposable` interface

The cleanup section is a chance to release **unmanaged** dependencies correctly, _system/native/db/cloud things..._ whatever C# should care of and that is not in the **garbage collector** scope.

```csharp
class GuyTalkingToWeirdo: IAsyncDisposable
{
	public async ValueTask DisposeAsync()
	{
		//await _weirdo.GoodBye()
	}

	public void DoMyDuties()
	{
	}
}
```


```csharp
{
	await using var guy = new GuyTalkingToWeirdos();
	
	guy.DoMyDuties();
}//implicit call to `await guy.DisposeAsync()`
```

## `"\e"`

That's a C#13 feature.

The escape character is used to type **ANSI sequences** to change text attributes such as colors, move cursor, clean screen and many other funny things that are gadget in nowadays web applications but that is still **nice to improve terminal output, and log reading.**
It used to be vital for terminal only applications that emulated windows and menus.

- `"\u001b"` is fine but somehow long to type, hence `"\e"` is better.

- `"\x1b"` is error prone because `"\x1babba is a cool band"` is not really what you expected, the hexa following the escape sequence get incorporated into the sequence itself **!!!danger!!!**

## Custom accessor

```csharp
class foo {

	public object this[int i]
	{
	    get { return _myPrivateArray[i]; }
	    set { _myPrivateArray[i] = value; }
	}

//index need not to be int, use whatever fits your need
	public object this[string k]
	{
	    get {
		    return _myPrivateDict.GetValueOrDefault(k)
		    //contract says object so better avoid return null
		    ?? default(DictElemType);
	    }
	    set { _myPrivateDict[k] = value; }
	}

//need to necessarily to define the set {} either....
}
```

## Multi-dimensional array

- Multi-dimensional arrays in C# can be measured with the `.Rank` property.
ie. `[,]` has **.Rank=2**  -  2 dimensions
while `[,,,,]` has **.Rank=5**  - 5 dimensions

- A dimension has a length that can be retrieved with `.GetLength(dimensionIndex)`

**Bonus:**
A Rank 2 array `[,]` (think of it as a matrix), can be converted to an array of array, for example with a class extension.

```csharp
using System.Numerics;

namespace App;

public static class ArrayHelper
{
    public static IEnumerable<IEnumerable<T>> ToArrays<T>(this T[,] matrix) where T : INumber<T>
    {
        for (var row = 0; row < matrix.GetLength(0); row++)
        {
            yield return matrix.GetArray(row);
        }
    }

    public static IEnumerable<T> GetArray<T>(this T[,] matrix, int row) where T : INumber<T>
    {
        for (var col = 0; col < matrix.GetLength(1); col++)
        {
            yield return matrix[row, col];
        }
    }


    public static IEnumerable<string> GetTop3
    (
        this IEnumerable<string> stockNames,
        IEnumerable<IEnumerable<float>> stocksPrices
    )
    {
        return stockNames.Zip(stocksPrices,

                (stockName, stockPrices) => {
                    var stockAvgPrice = stockPrices.Average();
                    return (stockName, stockAvgPrice);
                })

            .OrderByDescending(stock => stock.stockAvgPrice)
            .Take(3)
            .Select(stock => stock.stockName)
            .ToArray();
    }
}
  

public class UnitTest
{
    [Fact]
    public void Test_stocksHighestAverage()
    {

        string[] stockNames = [
            "a",
            "b",
            "c",
            "d"
        ];

        var stocksPrices = new float[,]
        {
            {10, 11, 12, 13, 14},
            {10, 11, 11, 13, 14},
            {10, 11, 13, 13, 14},
            {10, 11, 10, 13, 14}
        };

        var result = stockNames.GetTop3(stocksPrices.ToArrays());

        result.Should().BeEquivalentTo(["c", "a", "b"]);
    }
}
```


