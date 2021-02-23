

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
* set NiceHash QuickMiner to start with Windows and
* exit.


### 6. Startup with Windows?

If you would like NiceHash QuickMiner to startup with Windows, then you have to enable this option. Click on NiceHash QuickMiner Notification Tray Icon to open menu and then go to Settings and then check `Start with Windows`.


### 7. Additional tips and tricks?

I suggest going through the [list of tips and tricks](https://github.com/nicehash/NiceHashQuickMiner/wiki/Tips-&-tricks) and properly configure NiceHash QuickMiner for your video card(s), to maximize your mining reliability and your mining profits.