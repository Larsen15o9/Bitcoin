

### 1. Launch NiceHashQuickMiner.exe

If you have used `Installer` then you have probably created desktop shortcut for launching NiceHash QuickMiner. Just double click it to launch NiceHash QuickMiner and then go to step 2.

Otherwise if you have used `ZIP` file, then open folder where you extracted all files and start it by double clicking `NiceHashQuickMiner.exe`.

![Files](https://github.com/nicehash/NiceHashQuickMiner/blob/main/images/start.png?raw=true)


### 2. Allow UAC

Following screen may appear asking you to allow NiceHash QuickMiner. This is called UAC and it is for your protection. NiceHash QuickMiner needs administrative privileges to function correctly. You should press `Yes` button.

![Files](https://github.com/nicehash/NiceHashQuickMiner/blob/main/images/uac.png?raw=true)


### 3. Provide Mining Address

When NiceHash QuickMiner is started for the first time, it will ask you for your **NiceHash Mining Address**. There is a link and a picture how to get this address. **This is a very important step - this is how NiceHash QuickMiner gets linked with your NiceHash account, so it mines for you and not somebody else**.

You can get your NiceHash Mining Address on your [Mining page](https://www.nicehash.com/my/mining/rigs). If you do not have NiceHash account, you have to create one. The mining address will look like this:`34HKWdzLxWBduUfJE9JxaFhoXnfC6gmePG`. NiceHash QuickMiner will not let you enter wrong address, you just have to make sure that you are entering **your** address and not somebody else's.


### 4. Configure optional settings

This step is not mandatory but we strongly recommend not to skip it because it can greatly improve your mining experience. You can give your rig a name - this is useful when you have more than one rig. When you name each rig, you can quickly identify when one is giving you a problems. Another important thing is to choose appropriate Service Location. Generally, if the location is closer to you, then it is better, but this is not always true. You may experiment with it and see which location is best for you. How to do this is explained [here](https://github.com/nicehash/NiceHashQuickMiner/wiki/Tips-&-tricks#1-choose-your-service-location-to-improve-your-latency-and-reduce-number-of-stale-shares).

![Files](https://github.com/nicehash/NiceHashQuickMiner/blob/main/images/optsettings.png?raw=true)

If you intend to use your PC for constant mining, then it is recommended to check option to Autostart with Windows. Also set error handling action to Rig Reboot, because this is the only method to make the full recovery if your NVIDIA driver crashes. At the end, you can go to Rig Manager or OCTune. Clicking on any of these two buttons will save your configuration. Do note that it may take several minutes for your rig to appear in Rig Manager and be fully functional.


### 5. Configuring NiceHash QuickMiner

After NiceHash QuickMiner is started, all the interaction with it is done through menu at notification icon in your tray taskbar. Access it by **right clicking** on NiceHash QuickMiner icon.

![Tray icon](https://github.com/nicehash/NiceHashQuickMiner/blob/main/images/tray1.png?raw=true)

You can do following actions:
* start or stop mining,
* edit NiceHash QuickMiner config file (advanced),
* edit Excavator Command file (advanced),
* launch OCTune tool (explained here),
* enable or disable CPU mining,
* set NiceHash QuickMiner to start with Windows,
* activate or deactivate `Game Mode` and
* exit.


### 6. Optimize your GPU with one click!

When your rig appears in [Rig Manager](https://www.nicehash.com/my/mining/rigs) you can quickly optimize mining performance by clicking button `Optimize` and then choosing among three options:
- **Manual:** default mode, nothing is changed, NiceHash QuickMiner does not manage your GPU,
- **Lite:** mild optimisation is applied and
- **Medium:** average optimisation is applied.
![Tray icon](https://github.com/nicehash/NiceHashQuickMiner/blob/main/images/optimize_button.png?raw=true)

What does actually happen with your GPU when mining optimisation is applied? Following table explains for each GPU component what is happening. Do note that this table is very generalized and that each GPU might behave slightly differently.

Chosen optimisation | GPU core | VRAM | Fan speeds | Temperatures | Total power consumption | Hashrate speed
-------------------|----------|-----|----------|------------|---------------|-----
**Manual** | Stock clock | Stock clock | GPU Default | Very high | Very high | **Low**
**Lite**| Limited to very low value | Increased mildly | Keep GPU*<br>below 60 ℃ | Low | Low | **Medium**
**Medium**| Limited to low value | Increased moderately | Keep GPU*<br>below 60 ℃ | Low-Medium | Low-Medium | **High**

_* For RTX 3080 and RTX 3090 also keep VRAM Tjunction temperature below 95 ℃._

Optimisation feature is only available for RTX series and GTX 1660, 1660 Ti and 1660 Super. Do note that we are constantly trying to improve these optimizations which requires a lot of testing and performance measurements. Our numbers will surely improve in the future to offer you even better experience. To get latest optimisation applied for your GPU you only have to restart NiceHash QuickMiner. You can also view [latest raw data](https://github.com/nicehash/NiceHashQuickMiner/blob/main/optimize/data_002.json) that is being used.


### 7. Startup with Windows?

If you would like NiceHash QuickMiner to startup with Windows, then you have to enable this option. Click on NiceHash QuickMiner Notification Tray Icon to open menu and then go to Settings and then check `Start with Windows`.


### 8. Additional tips and tricks?

I suggest going through the [list of tips and tricks](https://github.com/nicehash/NiceHashQuickMiner/wiki/Tips-&-tricks) and properly configure NiceHash QuickMiner for your video card(s), to maximize your mining reliability and your mining profits.