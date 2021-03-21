# Why is this important? 
> Until this version, users with any NVIDIA GPU with GDDR5X had to risk using EthEnlargementPill to reach better speeds and efficiency. EthEnlargementPill is a protected closed source binary. For the operation it does not need internet connection. Therefore it is especially suspicious because it does connect to some servers when you would expect it not to use any network resources. The issue was raised some time ago [on Bitcointalk Forum](https://bitcointalk.org/index.php?topic=3370685.msg36788784#msg36788784). We are not saying that EthEnlargementPill is malicious, but considering being closed source, heavily protected and with only up to 100 lines of code that performs actual task while everything else is there for some unknown reasons, there are reasons to believe that not everything has been exposed what exactly this software does. **Therefore we suggest you should NEVER run EthEnlargementPill on a computer that contains any sensitive information such as any logins or passwords or on a computer that you intend to use for any work that requires any kind of privacy.** We were aware of the issue and worked hard to integrate this performance feature directly into NiceHash QuickMiner. Future versions will provide you with an automatic memory timings tuning.


### From version 0.4.2.0 - ability to modify certain memory timings 
Latest NiceHash QuickMiner has support for changing memory timings in OCTune! Set it and then save so it gets loaded every time Excavator is started up.
Download from here: https://github.com/nicehash/NiceHashQuickMiner/releases/download/v0.4.2.1_RC/NiceHash_QuickMiner_v0.4.2.1_RC.zip

Note: we do not have access to any private NVAPI where everything is explained. We are doing reverse engineering and these are our findings. What we have discovered so far is collected in the following table:

Timing | Remarks
-----|-------
RC | this must be >=(RP+RAS) 
RFC | considerable boost possible
RAS | considerable boost possible
RP | considerable boost possible
CL | 
WL | 
RD_RCD | 
WR_RCD | 
RPRE | 
WPRE | 
CDLR | 
WR | 
W2R_BUS | 
R2W_BUS | 
PDEX | 
PDEN2PDEX | 
FAW | EthEnlargementPill sets this to 16 (--revA sets to 20)
AOND | 
CCDL | 
CCDS | 
REFRESH_LO | 
REFRESH | considerable boost possible
RRD | EthEnlargementPill sets this to 4 (--revA sets to 5)
DELAY0 | 
ADR_MIN | 
WRCRC | 
OFFSET0 | 
DELAY0_MSB | 
OFFSET1 | 
OFFSET2 | 
DELAY0 | 

Unfortunately, changing memory timings works only on Pascal series. If anyone has any tips that would leave us to make this work on Turing and Ampere... there is a 0.2 BTC bounty for this piece of information!

Following cards are fully supported (tested):
- GP100 (Tesla)
- TITAN V
- TITAN Xp (not tested, but most likely)
- GTX 1080 Ti
- GTX 1080

From this version on, simply use timing name equal value to set timing. You can set multiple of them; example to set FAW to 16 and RRD to 4:
```
[{
		"time": 0,
		"commands": [{
				"id": 1,
				"method": "device.set.memory.timings",
				"params": ["0", "FAW=16", "RRD=4"]
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

Calling device.get or devices.get also returns actual timings for each GPU device, example:
```
...
"gpu_memory_timings":
{
    "bEditable": false,
    "timings": {
        "RC": 78,
        "RFC": 210,
        "RAS": 52,
        "RP": 26,
        "CL": 24,
        "WL": 5,
        "RD_RCD": 26,
        "WR_RCD": 16,
        "RPRE": 0,
        "WPRE": 1,
        "CDLR": 9,
        "WR": 27,
        "W2R_BUS": 7,
        "R2W_BUS": 7,
        "PDEX": 12,
        "PDEN2PDEX": 2,
        "FAW": 16,
        "AOND": 0,
        "CCDL": 2,
        "CCDS": 2,
        "REFRESH_LO": 5,
        "REFRESH": 4,
        "RRD": 4,
        "DELAY0": 12,
        "ADR_MIN": 6,
        "WRCRC": 16,
        "OFFSET0": 39,
        "DELAY0_MSB": 0,
        "OFFSET1": 13,
        "OFFSET2": 7
    }
},
...
```