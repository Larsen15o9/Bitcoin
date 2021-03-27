## How to get a good speed with GeForce GTX 1080 (Ti)? ~45 MH/s!

1. Download latest release from [here](https://github.com/nicehash/NiceHashQuickMiner/releases).
2. Install or unzip.
3. Run _NiceHashQuickMiner.exe_.
4. Your AV (or Windows Defender) might interfere here claiming software is PUA (potentially unwanted application). **You need to make sure to allow _NiceHashQuickMiner.exe_ and _excavator.exe_. Not doing this step may result in unexpected behavior - most likely mining will not work at all.**
5. First dialog after starting app will ask you for your NiceHash Mining Address. Login to NiceHash and go to the [Rig Manager](https://www.nicehash.com/my/mining/rigs). Click on the button `MINING ADDRESS` (check picture below). The long code displayed is your Mining Address.

![Mining Address](https://github.com/nicehash/NiceHashQuickMiner/blob/main/images/miningaddr.png?raw=true)

6. Next dialog is optional and you can skip it, but we suggest not to - set name of your worker and error handling mechanism. Do not enable start with Windows before you select your mining optimization profile (next step) - you have to test your optimization first!
7. At the end, go to the [Rig Manager](https://www.nicehash.com/my/mining/rigs) again where you should see your mining Rig. Click on it and a list of mining devices will be displayed.

![Optimize](https://github.com/nicehash/NiceHashQuickMiner/raw/main/images/optimize_button.png?raw=true)

8. You can control each mining device - start or stop it and apply [mining optimization profiles](https://github.com/nicehash/NiceHashQuickMiner/wiki/One-click-Optimizations).
9. Select optimization that you prefer. Boom! Your GeForce GTX 1080 or GTX 1080 Ti will suddenly hash much faster. **Up to 32 MH/s is expected for GeForce GTX 1080 and up to 45 MH/s for GeForce GTX 1080 Ti**, depending on optimization selected.
10. Selected optimization is automatically saved and will be loaded next time you launch NiceHash QuickMiner. When you quit NiceHash QuickMiner, mining optimization is removed. You do not have to use any OC tools at all.

### Troubleshooting
***
### Not getting expected speed?
Is your GPU primary GPU with display connected? Then [read here](https://github.com/nicehash/NiceHashQuickMiner/wiki/FAQ#-7-does-having-display-connected-to-the-video-card-have-any-effect-on-performance).