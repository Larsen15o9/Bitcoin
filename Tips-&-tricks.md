### 1. Optimize performance of your video cards for mining

**This has never been so easy!** It is strongly suggested that you optimize your video card to near perfect settings for mining using [OPTIMIZE button](https://github.com/nicehash/NiceHashQuickMiner/wiki/One-click-Optimizations). 


### 2. Choose your service location to improve your latency and reduce number of stale shares

**IMPORTANT: It is best to leave this value at `-1` (Automatic). NiceHash QuickMiner will choose best location and also swap to the next best one if your current best location is in maintenance. Please, be patient as the process of testing best location may take up to 15 minutes, depending on the mining hardware you have. During this time you may see periods of high latency which is completely normal.**

Open nhqm.conf (NiceHash QuickMiner right click notification icon and choose `Settings` -> `Edit config file`) and modify `"serviceLocation"`. Following locations are possible:
* Europe (Belgium): `0`,
* USA (California): `1`,
* Europe (Finland): `2`,
* USA (Virginia): `3`.

In the near future, more locations will be possible to choose from. After saving the config file, your mining location will be updated almost instantly. Observe latencies from accepted shares in Excavator console.

![Latency picture](https://github.com/nicehash/NiceHashQuickMiner/blob/main/images/latency.png?raw=true)

The numbers marked with red squares must be as low as possible. Experiment with serviceLocation until you get the best result.


### 3. Change your worker name

If you have more mining PCs, you can set name for each one. You can do this online through [Rig Manager](https://www.nicehash.com/my/mining/rigs) or locally through config. Open nhqm.conf (NiceHash QuickMiner right click notification icon and choose `Settings` -> `Edit config file`) and modify `"workerName"`. Name should only contain alphanumeric characters of English alphabet and max length is 15 characters.


### 4. Define what happens when something goes wrong

Mining by itself is very unstable process because hardware is pushed to the limits. Something can always go wrong. NiceHash QuickMiner will in most cases take care of all the issues, but sometimes, it cannot do on it's own and needs your command. There are two scenarios that can happen and three possibilities how NiceHash QuickMiner can react.

Scenario | Possible action | Config name | Default action
---------|-----------------|-------------|---------------
Excavator shows abnormally high speed | Do nothing `1`<br>Restart Excavator `2`<br>Restart PC `3`<br>Restart driver `4` | `"whenDeviceSpeedTooHigh"` | `2`
Excavator shows speed zero | Do nothing `1`<br>Restart Excavator `2`<br>Restart PC `3`<br>Restart driver `4` | `"whenDeviceSpeedZero"` | `2`
No GPU devices detected | Do nothing `1`<br>Restart Excavator `2`<br>Restart PC `3`<br>Restart driver `4` | `"whenNoDevices"` | `1`
 
When device is malfunction and not mining, Error will be displayed in [Rig Manager](https://www.nicehash.com/my/mining/rigs) as visible on the following picture.

![Device error](https://github.com/nicehash/NiceHashQuickMiner/blob/main/images/error.png?raw=true)

We suggest you to try to set action to number `2` (Restart Excavator). If that does not help and resolve the issue automatically, then set this to number `3`.  The above mentioned config values can be found in nhqm.conf (NiceHash QuickMiner right click notification icon and choose `Settings` -> `Edit config file`).

_Too high speed_ is defined with property `maxDeviceSpeed` which is 300 by default. This means that speed 300 MH/s is considered being too high and unreal thus some action is going to be taken to fix the error state. According to our tests, it is best to leave this value intact as it also works fine with fastest RTX 3090 cards (120 MH/s). If some day faster GPUs are introduced, then this value would have to be raised.


### 5. Enable logging for better troubleshooting

From version 0.4.0.0 on, you can enable/disable logging with a click of a button. After that you can export all important logs into a single .ZIP file with a click of a button as well.

![Logging](https://github.com/nicehash/NiceHashQuickMiner/blob/main/images/logs_enable.png?raw=true)

When something does go wrong, it can be fixed in most cases, but enough information is needed. We suggest you to enable file logging when you have problems. You can do this by modifying nhqm.conf (NiceHash QuickMiner right click notification icon and choose `Settings` -> `Edit config file`). Set `"fileLogLevel"` to `0` and also change `"launchCommandLine"` for Excavator to `"-wp 18000 -d 2 -f 0"` (note the last number changed to zero). This will enable both (NiceHash QuickMiner and Excavator full file logging). When submitting [issue here](https://github.com/nicehash/NiceHashQuickMiner/issues), it is strongly suggested to also provide these logs so the issue can be identified and resolved faster. Do not forget to **remove your personal information** from logs (such as your Mining Address) before you submit them.

Log level number | Log what?
-----------------|-----------
0 | log everything (TRACE)
1 | log debug (DEBUG)
2 | standard (INFO)
3 | warnings (WARNING)
4 | errors (ERROR)
5 | fatal (FATAL)
6 | no logging (disabled)


### 6. Use OCTune to overclock your video cards to improve efficiency and mining income

When simple OPTIMIZE button is not enough anymore and you want to explore the world of tuning for mining, learn how to use [OCTune](https://github.com/nicehash/NiceHashQuickMiner/wiki/OCTune) - the only tool you will ever need to push your cards to the max efficiency or max speed.


### 7. BIOS settings for larger rigs and rigs using PCIe risers

When you are running cards over risers, this adds extra instability factor to your configuration. You need to make sure your risers (comm link between CPU and GPU) are max stable. To achieve this, you need to set PCI Generation to 1 in BIOS (or at least 2). Having higher Generation introduce more instability because communication between CPU and GPU is faster and there are more chances for something to go wrong. There is no speed penalty when running Gen1 - your cards will hash at the same speed.

If one of your cards crashes during mining and you see device `ERROR` it most likely means riser instability. This is especially true, if it happens when your card is not overclocked. In this case replace riser, cable and set PCIE gen1 in BIOS.

When running more than 4 video cards, you will also have to set `Above 4G decoding` to `Enabled` in your motherboard's BIOS.


### 8. Enable automatic updates of RC versions

If you would like to receive RC updates as soon as they are available, then in config file `nhqm.conf` flip the switch `"bUpdateRCVersion"` to `true`. If you decide to participate in testing of early new versions, please, submit all found bugs [here](https://github.com/nicehash/NiceHashQuickMiner/issues). Thank you!


### 9. Improve mining performance with Windows settings

We were notified by our users that if you are using same video card for mining and rendering desktop, you can significantly improve mining performance and rendering of the desktop by turning on **Hardware-accelerated GPU scheduling**.

![hwaccelschedule](https://github.com/nicehash/NiceHashQuickMiner/blob/main/images/desktop_performance.png?raw=true) 

Open **Windows Settings**, then go to **Display** -> **Graphics settings** and turn on switch as visible in the picture above. Reboot and you should see significant improvement.


### 10. Enable TCC driver mode if possible

If you are using Tesla, Quadro or TITAN video cards for mining and that video card is not used for rendering display, you should enable TCC driver mode to improve performance and stability. You can do that using [nvidia-smi](https://docs.nvidia.com/gameworks/content/developertools/desktop/tesla_compute_cluster.htm). After you make a change, reboot is required.