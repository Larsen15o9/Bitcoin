# Why is this important? 
> Until this version, users with any NVIDIA GPU with GDDR5X had to risk using EthEnlargementPill to reach better speeds and efficiency. EthEnlargementPill is a protected closed source binary. For the operation it does not need internet connection. Therefore it is especially suspicious because it does connect to some servers when you would expect it not to use any network resources. The issue was raised some time ago [on Bitcointalk Forum](https://bitcointalk.org/index.php?topic=3370685.msg36788784#msg36788784). **You should NEVER run EthEnlargementPill on a computer that contains any sensitive information such as any logins or passwords or on a computer that you intend to use for any work that requires any kind of privacy.** We were aware of the issue and worked hard to integrate this performance feature directly into NiceHash QuickMiner. Future versions will provide you with an automatic memory timings tuning.


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