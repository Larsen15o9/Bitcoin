You might ask yourself, why would NiceHash create a miner that is very similar to the existing [NiceHash Miner](https://github.com/nicehash/NiceHashMiner)? The answer is explained on this page.

For NiceHash Miner to fully work, it relies on 3rd party plugins and miners. In most cases, these are programs of **unverified and unknown origin**. Authors of these programs are not known by their real names or there is no company that stands behind the software. Why developers of these programs keep their identity so private is unknown to us. There could be various reasons. Most likely, the reasons are not to harm miners, because they all charge developer fee for using their miner. But we cannot be fully sure that they have no intention of **ever** putting anything harmful inside their programs. Trusting them blindly would be a big mistake. That is why, if you want to use NiceHash Miner, you need to agree with that, confirm and acknowledge that and if these unknown developers really do something stupid one day, NiceHash cannot be held liable.

That means, if you use your PC for serious business, have important information on it or even coins or money, it is best **NOT** to use 3rd party miners from unknown origin. Luckily, NiceHash has created own miner in the past called [Excavator](https://github.com/nicehash/excavator). The code running is entirely developed in-house and NiceHash can vouch that there is nothing harmful inside. Another lucky factor is, that speeds Excavator reaches in daggerhashimoto (Ethereum mining) are completely comparable to other miners with devfee and when you also calculate in devfee, Excavator can be, in most cases, even more profitable than 3rd party miners.

But using Excavator on it's own is not so simple - you need to configure command files and prepare everything for your machine to work properly.

That is why we created another product for end user called NiceHash QuickMiner, which does all the **hard & tricky** configuration automatically so you just click buttons and don't have to worry about too deep technical stuff.

Because all the code of Excavator plus wrapper (QuickMiner) is made by NiceHash, there is no risk involved with anything harmful being put in. NiceHash is a public service, run by publicly known company from EU - Slovenia - H-BIT d.o.o., which means there are real people behind software. It is much easier to trust a software of known origin, because you know, that if there was anything harmful put in, there are people who could be held liable for it.

Now you know difference between NiceHash Miner and NiceHash QuickMiner. The choice at the end is yours. You need to ask yourself: **Do I want my PC to be fully secure when I install miner?** If the answer is YES, then you should install NiceHash QuickMiner. If you do not have any sensitive information on your PC or you do not care about that, you can go with NiceHash Miner.

# Main features
- It uses ONLY Excavator for GPU mining and XMRig for CPU mining. Excavator is in-house developed miner and is 100% free of any malware and XMRig is open source CPU miner. There are some more open source C# libraries used. Code running as NiceHash QuickMiner is either developed by NiceHash or used from public repositories which means it is 100% safe and you do not have to worry about exposing your PC's sensitive data or getting infected with malware. NiceHash QuickMiner will (in the future) NEVER use any closed source software, software of unknown or unverified origin. List of modules & libraries is at the end of this page.
- No benchmarks, you start mining IMMEDIATELY.
- No third party tools for GPU overclocking needed. NiceHash QuickMiner has its own powerful and quick tool for setting overclocks and fan speeds.
- Determine best overclock easily and quickly as never before with OCTune.
- Watchdog which takes care of restarting mining process if something fails.
- Windows autostart methods.
- Automatic updates.
- No developer fees. There is only NiceHash 2% pool-side fee with PPS (pay-per-share) payout scheme.

# Extra libraries & modules used
* C++ program Excavator entirely made by NiceHash: https://github.com/nicehash/excavator
* C# .NET library log4net: https://logging.apache.org/log4net/index.html
* C# .NET library managedCuda: http://kunzmi.github.io/managedCuda
* C# .NET library Microsoft.Win32.TaskScheduler: https://github.com/dahall/TaskScheduler#main-library
* C# .NET library websocket-sharp: https://github.com/sta/websocket-sharp
* XMRig miner (https://github.com/xmrig/xmrig); we have compiled version 6.7.0 with some modifications. The miner is stored in Excavator and it is extracted and launched when needed for CPU Mining.
* XMRig miner uses signed driver WinRing0x64.sys. This driver has been signed on Saturday, 26 July 2008 by Noriyuki MIYAZAKI. We do not have source for it, however, we believe that this driver pose no security threat at all as it has good reputation by Microsoft and has been used by various software for almost 13 years already.