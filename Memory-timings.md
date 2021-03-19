# Why is this important? 
> Until this version, users with any NVIDIA GPU with GDDR5X had to risk using EthEnlargementPill to reach better speeds and efficiency. EthEnlargementPill is a protected closed source binary. For the operation it does not need internet connection. Therefore it is especially suspicious because it does connect to some servers when you would expect it not to use any network resources. The issue was raised some time ago [on Bitcointalk Forum](https://bitcointalk.org/index.php?topic=3370685.msg36788784#msg36788784). We are not saying that EthEnlargementPill is malicious, but considering being closed source, heavily protected and with only up to 100 lines of code that performs actual task while everything else is there for some unknown reasons, there are reasons to believe that not everything has been exposed what exactly this software does. **Therefore we suggest you should NEVER run EthEnlargementPill on a computer that contains any sensitive information such as any logins or passwords or on a computer that you intend to use for any work that requires any kind of privacy.** We were aware of the issue and worked hard to integrate this performance feature directly into NiceHash QuickMiner. Future versions will provide you with an automatic memory timings tuning.


### From version 0.4.2.0 - ability to modify certain memory timings 

You can already start using this feature manually by editing _commands.json_ file. Example of _commands.json_ file which modifies timings for GPU0:
```
[{
		"time": 0,
		"commands": [{
				"id": 1,
				"method": "device.set.memory.timings",
				"params": ["0", "__MT0=16", "__MT1=4"]
			}]
	}, {
		"time": 20,
		"commands": [{
				"id": 1,
				"method": "workers.reset.all",
				"params": []
			}]
	}, {
		"time": 30,
		"loop": 30,
		"commands": [{
				"id": 1,
				"method": "worker.print.efficiencies",
				"params": []
			}]
	}, {
		"time": 1,
		"loop": 4,
		"commands": [{
				"id": 1,
				"method": "devices.smartfan.exec",
				"params": []
			}]
	}, {
		"event": "on_quit",
		"commands": []
	}, {
		"event": "on_quickminer.start",
		"commands": []
	}, {
		"event": "on_quickminer.stop",
		"commands": []
	}]
```


### What we have discovered so far.

Note: we do not have access to any private NVAPI where everything is explained. We are doing reverse engineering and these are our findings.

Code Name | Real Name |Known values | Remarks
-----|-------|-------|----------
__MT0 | FAW | 24, 20, 16 | GDDR5X has this value 24 or 20 (1080 Ti or 1080). Set to 16 for better performance. Multiple of RRD.
__MT1 | RRD | 6, 5, 4 | GDDR5X has this value 6 or 5 (1080 Ti or 1080). Set to 4 for better performance.

Following memory timings will be available with the next version:
```
	{ "RC", 0, 7, 0 },
	{ "RFC", 0, 9, 8 },
	{ "RAS", 0, 7, 17 },
	{ "RP", 0, 7, 24 },
	{ "CL", 1, 6, 0 },
	{ "WL", 1, 7, 7 },
	{ "RD_RCD", 1, 6, 14 },
	{ "WR_RCD", 1, 6, 20 },
	{ "RPRE", 2, 4, 0 },
	{ "WPRE", 2, 4, 4 },
	{ "CDLR", 2, 7, 8 },
	{ "WR", 2, 7, 16 },
	{ "W2R_BUS", 2, 4, 24 },
	{ "R2W_BUS", 2, 4, 28 },
	{ "PDEX", 3, 5, 0 },
	{ "PDEN2PDEX", 3, 4, 5 },
	{ "FAW", 3, 8, 9 },    // EthEnlargementPill timing 1
	{ "AOND", 3, 7, 17 },
	{ "CCDL", 3, 4, 24 },
	{ "CCDS", 3, 4, 28 },
	{ "REFRESH_LO", 4, 3, 0 },
	{ "REFRESH", 4, 12, 3 },
	{ "RRD", 4, 6, 15 },    // EthEnlargementPill timing 2
	{ "DELAY0", 4, 6, 21 },
	{ "ADR_MIN", 5, 3, 0 },
	{ "WRCRC", 5, 7, 4 },
	{ "OFFSET0", 5, 6, 12 },
	{ "DELAY0_MSB", 5, 2, 18 },
	{ "OFFSET1", 5, 4, 20 },
	{ "OFFSET2", 5, 4, 24 },
	{ "DELAY0", 5, 4, 28 },
	{ nullptr, 0, 0, 0 }
```
Unfortunately, changing memory timings works only on Pascal series. If anyone has any tips that would leave us to make this work on Turing and Ampere... there is a 0.2 BTC bounty for this piece of information!