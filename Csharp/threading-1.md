# Threading Cakes in C-sharp

![logo](../pix/viiinzzz48.png){: style="float: left"}
*Մι∩z•thedev* · [Follow](mailto:vinz.thedev@gmail.com)
Published in *Coding* · 6 min read · 1 day ago
___
<span style="font-size:2.5em">👏</span>65k <span style="font-size:2.5em">💬</span>321 <span style="font-size:2.5em">🔖</span> <span style="font-size:2.5em">⤴️</span>
___

## Producer/Consumer approach

Let's take the following Kata:  "The goal for the program is to simulate a cake factory."

Ultimately we need to optimize 100 cakes making, as fast as possible.

A cake is ready when the following 3 steps are accomplished :

    preparation : duration 2 seconds
    baking : duration 3 seconds
    wrapping : duration 1 second
    
The rules :
·   I can prepare 3 cakes simultaneously
·   I can cook 4 cakes simultaneously
·   I can wrap 2 cakes simultaneously


 - Either you consider the task literally and apply the KISS principle. 
	 In that case a valid approach, would be to do the GCD and prepare processing queues and aggregation points as per follow.
	 
```md
                                    . Timing
----------+-------+-------+--------------------
	PREP1 | PREP2 | PREP3 | PREP4     Prepare
	X X X | X X X | X X X | X X X   . 2 seconds
	                                .
------------+-----------+----------------------
	OVEN1   |   OVEN2   |   OVEN3     Bake
   X X X X  |  X X X X  |  X X X X  . 3 seconds
                                    .
                                    .
------+-----+-----+-----+-----+----------------
  W1  | W2  | W2  |  W4 |  W5 |  W6   Wrap
  X X | X X | X X | X X | X X | X X . 1 second
-----------------------------------------------
                           12 cakes .

. Prepare1  idle    +
.           idle    | Ramp-up cycle
idle        . Bake1 +
. Prepare2  .          +
.           .          | Full load cycle . 3 seconds
. Wrap1     . Bake2    +
. Prepare3  .
.           .
. Wrap2     . Bake3
. Prepare4  .
.           .
(...)
```

- Hence a complete optimal processing unit would consist of 4 preparation subunits, 3 oven subunits, and 6 wrapping subunits, it would produce 12 cakes every 6 seconds.
- We opportunely notice cycles can overlap, ie. prepare ahead of time while baking. We should also consider preparing and wrapping activities are mututally concurrent, a single operator supervise them. Hence chained cycles would take only 3 seconds
- The requirement says 100 cakes as fast as possible. With 1 processing unit it would take 100 / 12 = 9 cycles in 27 seconds.
- If not fast enough, and if we can afford provisioning several processing units, and staff several operators, we can of course decrease the overall processing time by as many fold.

Now what if the factory has many activities with different mutually exclusion schemes and variable execution durations, what if subunits cost limit their numbers, may turn down for maintenance and plenty other fancy...

To me this approach would be satisfactory for factory activities where predictability is high and process almost never changing. In the IT world of remote/async/timeout/error/retry,  a scalable composite distributed task would require a much more adaptive code.

- I published a POC based the producer/consumer paradigm with multiple lanes : https://github.com/viiinzzz/GateauKata
