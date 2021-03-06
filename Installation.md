Downloading and installing NiceHash QuickMiner is performed in following steps. **NEWS:** You can now use [download-installer](https://github.com/nicehash/NiceHashQuickMiner/releases/download/v0.5.1.3/NiceHashQuickMinerInstaller.exe) which performs all the steps below automatically. After you install it, simply go to [the next page - running NiceHash QuickMiner for the first time](https://github.com/nicehash/NiceHashQuickMiner/wiki/Starting-for-the-first-time).

### 1. Choosing version and downloading from GitHub

There are two versions of NiceHash QuickMiner: `stable` and `RC`. If you just want a reliable miner, to just install everything, set it up and forget about it as money comes in, then choose `stable` version. But if you want to get something more (perhaps faster speed, or other improvements) or if you wish to participate in testing NiceHash QuickMiner, then choose `RC` version.

Go to the [release page](https://github.com/nicehash/NiceHashQuickMiner/releases) and search for the latest version of your choice. When you have located the latest version, you need to download `.zip` file (not `.nhpkg`). Your browser may give you a warning that you are downloading dangerous content and would not let you to download it. In that case, you need to turn off this protection temporary in browser settings (how to do that, depends on browser, so I suggest searching for it on Google).

### 2. Verifying authenticity of the downloaded file

It is **strongly** recommended that you verify that the downloaded file is authentic. You can do that by following instructions [here](https://github.com/nicehash/NiceHashQuickMiner/tree/main/checksums). If the file is authentic, you can proceed to the next step.

### 3. Extracting the downloaded `.zip` file

Windows 10 already has built-in _unzipper_, so just right click on downloaded file and choose `Extract All...`. You can extract files to any path you like.

After that is done, you shall proceed to [running NiceHash QuickMiner for the first time](https://github.com/nicehash/NiceHashQuickMiner/wiki/Starting-for-the-first-time).

### 4. Optional: Remove previous version

NiceHash QuickMiner has auto updater and will notify and install when there is new version so you do not have to manually install it again. But if for some reason, you are doing that, you have to uninstall previous version first. You can do that manually by removing all autostart tasks (remove autostart methods in QuickMiner) and removing all files or you can run `NiceHashQuickMiner.exe --uninstall` and everything will be done automatically for you.