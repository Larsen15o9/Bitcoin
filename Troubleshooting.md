### Error #102 Excavator.exe is missing.
Most likely your Antivirus (AV) or Microsoft Defender has deleted it. Make sure to add exception for following files:
* excavator.exe,
* NiceHashQuickMiner.exe and
* xmrig.exe


### Warning #103 Your PC does not have enough Virtual Memory set. 
This can cause mining failure. Increase your Virtual Memory size to at least 6000 MB times number of GPUs your PC has. Read [here](https://www.nicehash.com/blog/post/how-to-increase-virtual-memory-on-windows) how to increase Virtual Memory size.


### Excavator WARNING Device #X-X could not obtain power consumption!
Excavator is not capable of getting information about power consumption, therefore some functionality may not work (correctly). Fully reinstall your NVIDIA drivers to fix this issue. From version 0.4.1.3, this issue has been fixed and it shall not appear anymore. Certain laptops may give you this warning - there is no solution because power management on some laptops is not available at all.


### Poor performance on GTX 1060, 1070 (Ti), 1080 (Ti).
Make sure to update to the latest version of QuickMiner and experiment with different [OPTIMIZE profiles](https://github.com/nicehash/NiceHashQuickMiner/wiki/One-click-Optimizations). Not all may work for you, but you shall find at least one that would give you satisfying results.

Do not use EthEnlargementPill and do not force CUDA to P0 state - that is not needed with latest version and would only break things apart. If you would like to further tune OC settings, you should do so by changing [memory timings](https://github.com/nicehash/NiceHashQuickMiner/wiki/Memory-timings). You may reach considerable speed improvements doing so.


### When I do CPU mining, my CPU isn't fully loaded.
By default, NiceHash QuickMiner starts XMRig with 50% load hint. This can be easily changed to 100% or any other number in `nhqm.conf` by modifying extra launch parameters and providing hint for 100% load:
```
...
"CPUMinerELP":"--cpu-max-threads-hint 100 --print-time 15",
...
```


### Excavator cannot connect and repeats warning _handshake declined by remote peer_.

Some routers/firewalls/modems may be blocking NiceHash domains. In that case, you have to check network security settings of your devices. In one particular case, someone had to disable `Cyber Security` on his _Century Link Modem_. Also note that this issue should be completely fixed in versions v0.3.2.6 and later as mining domains are now resolved using DNS over HTTPS.


### I get NVML related error.
![NVML Error](https://github.com/nicehash/NiceHashQuickMiner/blob/main/images/nvml_error.png?raw=true)

If you get error like this, then following is possible:
- You do not have [supported hardware](https://github.com/nicehash/NiceHashQuickMiner/wiki/Supported-hardware) - NiceHash QuickMiner works only on NVIDIA video cards, it does not support AMD video cards!
- Your driver has just been updated; in that case, a simple restart of your PC will resolve the issue.
- You are using very old NVIDIA drivers. Update to the latest NVIDIA driver to fix the issue.


### NiceHash QuickMiner starts with Windows too quickly. Can I delay it?
Yes, you can. Open Task Scheduler (write `Task Scheduler` in your search bar). Then follow markings from 1 to 4 from the picture below. Once you choose your wanted delay just close the dialog by pressing `OK`. Next time you are booting Windows, NiceHash QuickMiner would start with adjusted delay.
![Task Scheduler](https://github.com/nicehash/NiceHashQuickMiner/blob/main/images/ts_delay.png?raw=true)


### I am using another tool for managing my video card's fans (such as MSI Afterburner) and fan speed is occasionally reset to automatic. How can I fix this?
The problem is in default _commands.json_ file shipped with version 0.4.1.3. This file commands that all fans are reset to automatic behavior when Excavator exits. You may have some instability and Excavator is occasionally restarted. This means automatic fan profile is applied every time this happens. To prevent this, you can either modify _commands.json_ on your own or use [this one with fan reset removed](https://github.com/nicehash/NiceHashQuickMiner/blob/main/optimize/default_commands.json). If you wish to also remove Excavator's memory set to 0 delta clock for the time of generating DAG (so the DAG does not get corrupted), then Excavator needs to be launched with `-g` switch; In file _nhqm.conf_ modify default `"launchCommandLine" : "-qx -qm  -d 2 -f 6"` by adding `-g` so then it looks like this: `"launchCommandLine" : "-qx -qm -d 2 -f 6 -g"`. We do not recommend doing this, because it is well known that DAG gets corrupted when memory clock is too high and this feature is more or less a necessity to avoid getting shares above target.


### When I start NiceHash QuickMiner, it does not mine but just idles.
NiceHash QuickMiner goes into last state before you closed it. If you stopped mining before closing it, then it would not start mining when you turn it on again. If you wish to start mining when you start NiceHash QuickMiner, then before you close it, **do not stop mining**. If you want to start mining at Windows boot-up, then before you turn PC off or restart, do not stop mining, but rather just perform restart or shut down of your PC. Next time NiceHash QuickMiner is started, it will start mining automatically.


<a name="defender-issue"></a>
### Windows Defender is blocking NiceHash QuickMiner / I get notification that excavator.exe was blocked from running
Microsoft Windows Defender may sometimes unjustly flag _NiceHashQuickMiner.exe_ and/or _excavator.exe_ as PUA (Potentially Unwanted Application) regardless the fact that both of these applications are signed by the Extended validation (EV) code signing certificates. This is especially issue with every new released version. After some time, this issue is resolved, because enough people make exceptions. PUA flag is removed because its reputation based system says that enough people **trust** the application so it does not have to be flagged as PUA anymore. When you get notification that any part of NiceHash QuickMiner has been blocked by Microsoft Windows Defender, select to allow the file on this device. Your action contributes making NiceHash QuickMiner less likely be falsely flagged as PUA. If you never get these warnings, then check configuration of your Microsoft Windows Defender as displayed:
![Windows Defender](https://github.com/nicehash/NiceHashQuickMiner/blob/main/images/pua.png?raw=true)
1. Open _App & browser control_ and then _Reputation-based protection_. 
2. Under _Potentially unwanted app blocking_ make sure you have selected `Block apps` and `Block downloads`.
3. Next time you download and/or launch NiceHash QuickMiner, you will be notified about PUA and asked to make an action. Select to _Allow on device_. You might be asked to make this action several times for multiple files.
We appreciate your contribution towards increased positive reputation for NiceHash QuickMiner. Thank you!


### NiceHash QuickMiner selects mining location with high ping instead of location with low ping. Automatic service location select does not work correctly.
The algorithm works by testing each location sending and getting back response for at least 8 shares. Then the share with minimal latency is selected as latency for that location. There are currently four locations. This means, if you have only one slow video card, it may take a while to properly test all available locations (up to 15 minutes). Do not worry if you see high ping for a while - it is only testing phase. When the testing phase is over, NiceHash QuickMiner would always use location with the lowest latency. If there is maintenance at your best location, NiceHash QuickMiner would pick second best location according to the measured latency. Because network conditions may change over time, this test is performed once every week.


### When trying to apply OPTIMIZE, I get error _Not initialized yet_
This error would appear if no data for OPTIMIZE is available. We may be constantly tuning OPTIMIZE data to better fit as much as possible cards therefore this data does not come statically with the miner but is rather downloaded and periodically updated by miner. The data is available here: https://github.com/nicehash/NiceHashQuickMiner/tree/main/optimize If QuickMiner is unable to download data, then you would get this error when trying to apply OPTIMIZE profile. Make sure that nothing is blocking your access to GitHub and that QuickMiner can freely download data from the internet.


### Unable to deactivate Game Mode.
This can happen if you update NVIDIA drivers during _Game Mode_ being activated. Please, make sure to turn off NiceHash QuickMiner before you update NVIDIA drivers. Unexpected behavior can happen if drivers are updated during mining because certain important handles/values can change and then completely break functionality of the software. If you do happen to update when NiceHash QuickMiner is running, then a simple reboot of your PC will solve the issue.


### Warning #104
Read about it [here](https://github.com/nicehash/NiceHashQuickMiner/wiki/MSI---Improve-stability-of-your-PC-Rig).