### Error #102 Excavator.exe is missing.
Most likely your Antivirus (AV) or Microsoft Defender has deleted it. Make sure to add exception for following files:
* excavator.exe,
* NiceHashQuickMiner.exe and
* xmrig.exe


### Warning #103 Your PC does not have enough Virtual Memory set. 
This can cause mining failure. Increase your Virtual Memory size to at least 6000 MB times number of GPUs your PC has. Read [here](https://www.nicehash.com/blog/post/how-to-increase-virtual-memory-on-windows) how to increase Virtual Memory size.


### Excavator WARNING Device #X-X could not obtain power consumption!
Excavator is not capable of getting information about power consumption, therefore some functionality may not work (correctly). Fully reinstall your NVIDIA drivers to fix this issue. From version 0.4.1.3, this issue has been fixed and it shall not appear anymore.


### Poor performance on GTX 1060, 1070 (Ti), 1080 (Ti).
You need to make sure, your card is running in P0 state. This can be achieved using some 3rd party tools as suggested in [this Reddit thread](https://www.reddit.com/r/RenderToken/comments/9w2rd9/how_to_use_maximum_p0_power_state_with_nvidia/).

Additionally, GTX 1080 and GTX 1080 Ti have GDDR5X memory which needs different memory timings for better performance. There is no publicly available code to do that, there are only closed source protected binaries of EthEnlargmentPill from unknown authors, which I do NOT suggest to use if you have any sensitive information.


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
The problem is in default _commands.json_ file shipped with version 0.4.1.3. This file commands that all fans are reset to automatic behavior when Excavator exits. You may have some instability and Excavator is occasionally restarted. This means automatic fan profile is applied every time this happens. To prevent this, you can either modify _commands.json_ on your own or use [this one with fan reset removed](https://github.com/nicehash/NiceHashQuickMiner/blob/main/optimize/default_commands.json).


### When I try to apply OPTIMIZE profile, I get error: _Not initialized yet_. How can I solve this problem?
In most cases, this happens if your miner is stopped and does not mine. QuickMiner needs to be mining to be able to apply OPTIMIZE profiles. If you do mine, then there is an issue getting OPTIMIZE data from GitHub servers. In this case, enable full logging and open an [issue](https://github.com/nicehash/NiceHashQuickMiner/issues), submit logs and we will take a look what can be done about it.


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
The algorithm works by testing each location sending and getting back response for at least 8 shares. Then the share with minimal latency is selected as latency for that location. There are currently four locations. This means, if you have only one slow video card, it may take a while to properly test all available locations (up to 15 minutes). Do not worry if you see high ping for a while - it is only testing phase. When the testing phase is over, NiceHash QuickMiner would always use location with the lowest latency. If there is maintenance at your best location, NiceHash QuickMiner would pick second best location according to measured latency. Because network conditions may change over time, this test is performed once every week.
