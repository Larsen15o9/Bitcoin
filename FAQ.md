# Questions:
[1. Why is NiceHash QuickMiner started with administrator privileges?](#faq01)<br>
[2. What happens when DAG is being generated?](#faq02)<br>
[3. Where can I see number of accepted and rejects shares?](#faq03)<br>
[4. Why do some jobs have "clean" suffix?](#faq04)<br>
[5. Does NiceHash QuickMiner overclock my cards by default?](#faq05)<br>
[6. How can I limit CPU mining to less cores/load?](#faq06)<br>
[7. Does having display connected to the video card have any effect on performance?](#faq07)<br>

# Answers:

### <a name="faq01"></a> 1. Why is NiceHashQuickMiner started with administrator privileges?

Administrator privileges are needed for overclocking. MSI Afterburner (which you'd not need anymore) is started with administrator privileges aswell. Since up to 20% extra performance is possible to achieve with up to 50% reduced power load, we do not believe it is smart to mine without adjusting clocks and power limits which require administrator privileges.

### <a name="faq02"></a> 2. What happens when DAG is being generated?

Excavator would set memory overclock to 0 for the time DAG is being generated. This is done to prevent generation of corrupted DAG which causes all future shares to be invalid. Note that this feature only works if you set your overclock with Excavator and it DOES NOT work when using MSI Afterburner for overclocking. With this feature you can clock your card higher and do not need to worry about corrupted DAGs because these cannot happen anymore.

### <a name="faq03"></a> 3. Where can I see number of accepted and rejects shares?

You can see number of accepted and rejected shares by calling [API method algorithm.list](https://github.com/nicehash/excavator/tree/master/api#algorithm-list). Note that, to the contrary of other PPLNS pools, for NiceHash, these values are not important. The reason is, because each share has a certain value that may not be the same. NiceHash does not have a fixed difficulty but rather dynamic. Higher difficulty shares have higher value. Since NiceHash has a PPS payout scheme (pay-per-share), it is very important to know the value of the share (share at twice the difficulty is worth twice as much BTC). If you chart down shares with their values, you get accepted/rejected speed. These charts are already available at NiceHash - Rig Manager. Other pools often display accepted speed on their charts as the value that the miner is reporting to the pool - and this value can be cheated-out (sending some extreme large value for example). NiceHash does not support speed reported by miner, rather it calculates accepted/rejected speed out of your shares. Thus, contrary to the other pools, these charts have very high value as they represent direct performance of your miner and your mining payouts are based directly on that.

### <a name="faq04"></a> 4. Why do some jobs have "clean" suffix?

When job has "clean" suffix, it means that miner needs to drop current job **immediately** and start working on the new job - all previous work is not valid anymore and would result in a rejected share (job not found - stale share). One of the miner qualities is defined by the amount of how much time it takes for it to drop current job and start working on the new one. The time in between receiving new clean job and start working on the new job is wasted as these found shares **always** result in rejection as stale shares. This quality is not visible by the reported hashing speed but rather as a calculated speed on server side (NiceHash - accepted speed -> your actual profitability) or rather amount of stale shares (also your high latency to server increase amount of stale shares). Excavator has this switching time in between 1-3 milliseconds on modern CPUs of latest generation (Intel 10th gen, AMD Ryzen, Threadripper). It can be also observed and calculated from logs (when full detailed logging with `-f 0` is enabled). This task is not so simple to optimize, because NVIDIA kernel launches are non preemptive, which means, once kernel is started, it cannot be terminated. Unfortunately, time-short kernel result in reduced speed because time is wasted managing kernel launch and finish. So, usually a certain balance is needed so that kernels do not take too long and cause a lot of wasted tame when jobs are switched and that also don't last too short time to waste mining time due to excessive kernel launch management. Of course, any miner developer can use various tricks to solve this issue and it is not only about tweaking these two values. Anyway... this is off topic now already. Back to "clean" jobs.

When job is **not** "clean" it means that miner **does not** have to drop current job, because previous job is still valid. Therefore when you see a job that isn't "clean" you know that it won't reduce your miner speed consequently. Excavator is made to simply ignore non-clean jobs (these only get printed out, but that's all).


### <a name="faq05"></a> 5. Does NiceHash QuickMiner overclock my cards by default?
**NO!** There is no overclocking done without explicit command from the user.


### <a name="faq06"></a> 6. How can I limit CPU mining to less cores/load?
By default, NiceHash QuickMiner starts XMRig with 50% load hint. This can be easily changed to 100% or any other number in `nhqm.conf` by modifying extra launch parameters and providing hint for whatever load you wish. If you provide 25, then XMRig will try to load 25% of your CPU, 50 then 50% etc.
```
...
"CPUMinerELP":"--cpu-max-threads-hint 50 --print-time 15",
...
```


### <a name="faq07"></a> 7. Does having display connected to the video card have any effect on performance?
Yes! When you have display connected to a GPU, there is some performance penalty and your GPU will not hash with max possible speed. How much you lose depends on many factors such as number of displays connected, output resolution, number and intensity of various applications that utilize your GPU (NiceHash QuickMiner is not the only application utilizing your video card). Sometimes the performance penalty can be very minimal and perhaps even hardly to notice. But it can also be severe - 10%, 15% or even 25% of your max hashrate may be lost due to this fact. There are number of possible alleviations to make the penalty less severe:
- Use integrated GPU for rendering display.
- [Turn off visual effects in Windows](https://www.windowscentral.com/how-disable-system-visual-effects-boost-performance-windows-10).
- Turn off `Hardware acceleration` in applications that use GPU such as Website browsers.
- Turn off/disable unneeded applications that utilize GPU.
- Reduce resolution and/or refresh rate.
- Reduce number of displays.