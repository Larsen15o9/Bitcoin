## Index
[1. Finding most efficient or the fastest combination of OC values for your card(s) - classic long path](#count01)<br>
[2. Alternative overclocking explained](#count02)<br>
[3. Autotune (experimental from v0.3.0.5) - very fast automatic OC tuning - 95% max efficiency guaranteed within 5 minutes!](#count03)<br>

## <a name="count01"></a> 1. Finding most efficient or the fastest combination of OC values for your card(s)

Use OCTune. Look for values `Min KT` and `Avg KT`. Your goal is to get these values as low as possible. What is the meaning of these values? KT = Kernel Time. It is execution time of code running on GPU in microseconds. Min = minimal time (in previous X runs) and Avg = average time. Min can sometimes drop down to half of usual - you should ignore these values.

_1. Find your max memory clock_
First, you should find your max memory speed or determine at what memory speed you are prepared to run your GPU. Higher power limit and lower core clock can help memory stability. Therefore, set power limit to some high value (can be at 100% of your TDP - note the value needs to be in Watts!) and core clock to -600. Then increase memory clock by 25 each step and test at least several minutes. There should be no `HW err` and make sure there are at least 3 accepted shares on that card (`HW ok` increases by 3 at that speed). Once you find your max memory clock, you can go to step 2.

_2. Reduce power limit_
Now you can start reducing power limit. At some point, `Min KT` and `Avg KT` will start rising. That is a sign that you need to back off and stop reducing power limit (temporary). Now you need to increase core clock. Go to step 3.

_3. Increase core clock_
Increase core clock +25 at a time until your `Min KT` and `Avg KT` stop improving (values do not go lower anymore). Note that higher core clock can affect stability of your memory. You may have to decrease your memory clock if there are rejected shares (share above target) and value in `HW err` increases. Once you find ideal core clock, you can again try with reducing power limit.

_4. Play with settings to achieve best KT values_
You have to fiddle with core clock, memory clock and power limit until you find best KT values (lowest) and max stability (no shares above target - `HW err` stays at 0). Once you find best values, you will have the highest possible speed. You can save your OC configuration (click `Save current configuration`) so it will be applied next time Excavator is started.

## <a name="count02"></a> 2. New OCTune (v0.3.0.4+) with alternative overclocking abilities

_Note: This feature is currently available only in `RC` version of NiceHash QuickMiner which can be obtained [here](https://github.com/nicehash/NiceHashQuickMiner/releases/tag/v0.3.0.6_RC)._

With version 0.3.0.4 alternative overclocking ability was added to NiceHash QuickMiner. With this method, you only need to provide two values to optimize your mining efficiency:
* absolute max core clock of video card,
* absolute memory clock of VRAM and
* fan speed (optional).

For comparison, UI is displayed here (1 is old classic method, 2 is new alternative method):
![OCTune Alt OC](https://github.com/nicehash/NiceHashQuickMiner/blob/main/images/octunealt.png?raw=true)

There are some differences and rules:
* You cannot use both OC methods at the same time. Whichever method is used last is applied and saved in `commands.json` (if wanted).
* Alternative OC resets TDP to default value of 100%. Your power limit entirely depends on configured core clock and memory clock of your video card.
* There is minimal core clock (210) for all cards.
* Alternative OC may not work on all NVIDIA series cards (but works confirmed on series 3000 and 2000).
* Alternative OC is the only way to optimize Quadro and Tesla series as these cards do not support changing delta core and delta memory clocks.

### Guide how to optimize your card using alternative OC (only about 5 min of time per card needed)

First, find max stable memory clock of VRAM. Generally, following memory clocks can be achieved on most of video cards:

GPU Model | Absolute memory clock | Delta memory clock
----------|-----------------------|--------------------
3060 Ti | 7900 | +1100
3070 | 7900 | +1100
3080 | 10300 | +850
3090 | 10350 | +850

If you are getting rejected shares of type `Share above target` then your memory clock is **not** stable and you have to reduce it. But generally, if you get one or two bad shares of such type per day, it is still okay.

Once you find max stable memory clock, start with high `Core clock limit` (like `1800` for example) and start decreasing it, observing **Speed (MH/s)**, **Power Real (W)** and **Eff. (kH/J)** (efficiency).

### If you want highest possible speed

After each decrease of `Core clock limit`, check values `Min KT`, `Avg KT` and `UMed KT`. These values should go as low as possible. The lower they are, the better speed you have. Once you are happy with the achieved speed, you can save your OC configuration by pressing `Save current configuration` button at the top. Note that if you change your memory clock, you'd need to readjust `Core clock limit` but usually not for much (perhaps only +15 or -15).

### If you want highest possible efficiency (recommended)

Highest possible efficiency makes your video card use less electricity, produce less heat and wear&tear while still maintaining almost max possible speed. Here, you should do reverse, start with lowest `Core clock limit` and increase +15 at a time. Observe how `KT` values are falling down. At one point, you will notice that `KT` values do not change much with further increases of `Core clock limit`. That is the time to stop. Job done. You can save your OC configuration now.

While testing few cards, we managed to achieve following numbers:
GPU Model | Absolute memory clock | Core clock limit | Power consumption (W) | Speed (MH/s) | Efficiency (kH/J)
---|---|---|---|---|---
3060 Ti | 7950 | 1350 | 120 | 60 | 500
3070 | 7950 | 1050 | 117 | 60 | 513
3090 | 10401 | 1080 | 286 | 117 | 411


## <a name="count03"></a> 3. Autotune (experimental from v0.3.0.5+)

Autotune takes user's input - `Memory clock (absolute)` and determines optimal `Core clock limit` so you get **best speed or efficiency**. The result could still be further tweaked for perhaps additional 1% of performance or efficiency, but considering that **Autotune** does everything automatically and very fast (just one iteration through viable core clock limits simultaneously testing for performance), there is serious question whether additional tweaking is even worth your time.

Autotune works through alternative OC method introduced in version 0.3.0.4. Besides providing absolute memory clock, user provides starting core clock and ending core clock limit. The smaller the interval, the less iterations are needed thus the algorithm can finish faster. But providing too small interval means you may "miss out" the possible better OC configuration. If you are a beginner, we suggest leaving these values intact and only start modifying them once you gain some experiences so you know what to expect from each video card.

Unfortunately, due to API limitations of NVIDIA management libraries, Alternative OC and Autotune features are available only for RTX series (2000 and 3000). Since Alternative OC works for **Quadro and Tesla** cards (as long as Memory clock is not changed), we expect Autotune to work for these cards as well, but we were not able to test that yet.

Autotune works much better on video cards that **do not** have display connected. If you have a chance to (at least temporary) connect display through another card (perhaps integrated one?), then we suggest doing so, because your results will be much better.

You might be wondering what kind of values to use for Memory clock. I have prepared some classification of low, medium and high clocks. You should start with low and then move onto medium and high if everything is working stable.

GPU Model | Default memory clock | Low memory clock | Medium memory clock | High memory clock
----------|----------------------|------------------|---------------------|-------------------
3060 Ti, 3070 | 6800 | 7500 | 7900 | 8100
3080 | 9250 | 9800 | 10300 | 10500
3090 | 9500 | 10000 | 10400 | 10600

For 2000 series cards, I believe you can use values written for 3060 Ti and 3070 as they all use same type of memory (GDDR6). Start with Low memory clocks and run Autotune to get best core clock limit. Then run this configuration for at least one day. If nothing crashes. Great, try with medium memory clock and repeat. Most of video cards should be able to handle clocks from medium class. But you may be unlucky (silicon lottery).