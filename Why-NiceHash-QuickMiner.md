You might ask yourself, why would NiceHash create a miner that is very similar to the existing [NiceHash Miner](https://github.com/nicehash/NiceHashMiner)? The answer is explained on this page.

For NiceHash Miner to fully work, it relies on 3rd party plugins and miners. In most cases, these are programs of **unverified and unknown origin**. Authors of these programs are not known by their real names or there is no company that stands behind the software. Why developers of these programs keep their identity so private is unknown to us. There could be various reasons. Most likely, the reasons are not to harm miners, because they all charge developer fee for using their miner. But we cannot be fully sure that they have no intention of **ever** putting anything harmful inside their programs. Trusting them blindly would be a big mistake. That is why, if you want to use NiceHash Miner, you need to agree with that, confirm and acknowledge that and if these unknown developers really do something stupid one day, NiceHash cannot be held liable.

That means, if you use your PC for serious business, have important information on it or even coins or money, it is best **NOT** to use 3rd party miners from unknown origin. Luckily, NiceHash has created own miner in the past called [Excavator](https://github.com/nicehash/excavator). The code running is entirely developed in-house and NiceHash can vouch that there is nothing harmful inside. Another lucky factor is, that speeds Excavator reaches in daggerhashimoto (Ethereum mining) are completely comparable to other miners with devfee and when you also calculate in devfee, Excavator can be, in most cases, even more profitable than 3rd party miners.

But using Excavator on it's own is not so simple - you need to configure command files and prepare everything for your machine to work properly.

That is why we created another product for end user called NiceHash QuickMiner, which does all the **hard & tricky** configuration automatically so you just click buttons and don't have to worry about too deep technical stuff.

Because all the code of Excavator plus wrapper (QuickMiner) is made by NiceHash, there is no risk involved with anything harmful being put in. NiceHash is a public service, run by publicly known company from EU - Slovenia - H-BIT d.o.o., which means there are real people behind software. It is much easier to trust a software of known origin, because you know, that if there was anything harmful put in, there are people who could be held liable for it.

Now you know the difference between NiceHash Miner and NiceHash QuickMiner. At the end, the choice is yours. You need to ask yourself: **Do I want my PC to be fully secure when I install cryptocurrency miner?** If the answer is YES, then you should install NiceHash QuickMiner. If you do not have any sensitive information in your PC, if you really don't care about any information in your PC getting exposed one day or if you don't care that your PC may be abused as a zombie client in a botnet one day, or abused for any illegal activity, you can go with NiceHash Miner which installs all those risky 3rd party miners of unknown origin. Generally, if you have a completely dedicated mining rig, which is used **only** for cryptocurrency mining and nothing else and you properly isolate it on your network, you should be fine with NiceHash Miner and 3rd party miners. In any other case, we suggest you to use NiceHash QuickMiner. If you have AMD cards and you want to keep your PC fully secure, our advice is to either use [open source ethminer](https://github.com/ethereum-mining/ethminer) or [lolMiner](https://github.com/Lolliedieb/lolMiner-releases), which is the only devfee miner that is not completely anonymous.

# Main features
* It uses **ONLY** [Excavator for GPU mining](https://github.com/nicehash/excavator) and **XMRig** for CPU mining. Excavator is in-house developed miner and is 100% free of any malware and [XMRig is open source CPU miner](https://github.com/xmrig/xmrig). There are some more open source C# libraries used. Code running under NiceHash QuickMiner is either developed by NiceHash or used from public repositories which means it is 100% safe and you do not have to worry about exposing your PC's sensitive data or getting infected with malware. NiceHash QuickMiner will (in the future) NEVER use any closed source software, software of unknown or unverified origin.
* No benchmarks, you start mining immediately.
* No third party tools for GPU overclocking needed. NiceHash QuickMiner has its own powerful and quick tool for setting overclocks and fan speeds named OCTune. Determine best overclock easily and quickly as never before with OCTune.
* Watchdog which takes care of restarting mining process if something fails.
* Windows autostart methods.
* Automatic updates.
* No developer fees. There is only NiceHash 2% pool-side fee with PPS (pay-per-share) payout scheme.
* Powerful and reliable one-click-optimisations for GTX 1660 and RTX series cards.
* Game Mode to quickly switch between mining and gaming.

# Drawbacks. Why it is better to use NiceHash Miner or NiceHash OS?
- NiceHash QuickMiner mines **only** daggerhashimoto (ethereum). There is no algorithm switching so there is no chance for extra above-ethereum payrate that may come occasionally. The amount being lost depends on your GPU Model, but currently, it may be only up to several percentage.

# Extra libraries & modules used
* C++ program Excavator entirely made by NiceHash: https://github.com/nicehash/excavator
* C# .NET library log4net: https://logging.apache.org/log4net/index.html
* C# .NET library managedCuda: http://kunzmi.github.io/managedCuda
* C# .NET library Microsoft.Win32.TaskScheduler: https://github.com/dahall/TaskScheduler#main-library
* C# .NET library websocket-sharp: https://github.com/sta/websocket-sharp
* C# .NET library DotNetZip: https://archive.codeplex.com/
* XMRig miner (https://github.com/xmrig/xmrig); we have compiled version 6.7.0 with some modifications. The miner is stored in Excavator and it is extracted and launched when needed for CPU Mining.
* XMRig miner uses signed driver WinRing0x64.sys. This driver has been signed on Saturday, 26 July 2008 by Noriyuki MIYAZAKI. We do not have source for it, however, we believe that this driver pose no security threat at all as it has good reputation by Microsoft and has been used by various software for almost 13 years already.