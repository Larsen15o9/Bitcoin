# Why is this important? 
> Until this version, users with any NVIDIA GPU with GDDR5X had to risk using EthEnlargementPill to reach better speeds and efficiency. EthEnlargementPill is a protected closed source binary. For the operation it does not need internet connection. Therefore it is especially suspicious because it does connect to some servers when you would expect it not to use any network resources. The issue was raised some time ago [on Bitcointalk Forum](https://bitcointalk.org/index.php?topic=3370685.msg36788784#msg36788784). We are not saying that EthEnlargementPill is malicious, but considering being closed source, heavily protected and with only up to 100 lines of code that performs actual task while everything else is there for some unknown reasons, there are reasons to believe that not everything has been exposed what exactly this software does. **Therefore we suggest you should NEVER run EthEnlargementPill on a computer that contains any sensitive information such as any logins or passwords or on a computer that you intend to use for any work that requires any kind of privacy.** We were aware of the issue and worked hard to integrate this performance feature directly into NiceHash QuickMiner. Future versions will provide you with an automatic memory timings tuning.


### From version 0.4.2.0 - ability to modify certain memory timings 
Latest NiceHash QuickMiner has support for changing memory timings in OCTune! Set it and then save so it gets loaded every time Excavator is started up.
Download from here: https://github.com/nicehash/NiceHashQuickMiner/releases/download/v0.4.5.0_RC/NiceHash_QuickMiner_v0.4.5.0_RC.zip

Note: we do not have access to any private NVAPI where everything is explained. We are doing reverse engineering and these are our findings. The only useful official documentation we got from NVIDIA regarding memory timings is their public information about [memory tweaks](https://nvidia.github.io/open-gpu-doc/MemoryTweakTable/MemoryTweakTable.html). What we have discovered so far is collected in the following table:

Timing | Remarks
-----|-------
RC | this must be >=(RP+RAS) 
RFC | considerable boost possible
RAS | considerable boost possible
RP | considerable boost possible
CFG0_R0 |
CL | 
WL | 
RD_RCD | 
WR_RCD |
CFG1_R0 |
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
CFG4_R0 |
ADR_MIN | 
CFG5_R0 |
WRCRC | 
CFG5_R1 |
OFFSET0 | 
DELAY0_MSB | 
OFFSET1 | 
OFFSET2 | 
DELAY01 | 

Unfortunately, changing memory timings works only on Pascal and Volta series. If anyone has any tips that would get us to make this work on Turing and Ampere... there is a **1 BTC bounty** for this piece of information!

Following cards are fully supported (tested):
GPU Model | Suggested timings
----------|--------------
GP100 (Tesla) | It has huge issues with TLB thrashing so you will not get much speed regardless of timings, but 1 GB DAG gives you 70+ MH/s
TITAN V | From 68 MH/s to 76 MH/s using following: "RC=45","RFC=251","RAS=23","RP=22","RD_RCD=10","FAW=12","REFRESH_LO=7","REFRESH=10","RRD=3"
TITAN Xp | not tested yet, but most likely works
GeForce GTX 1080 Ti | "FAW=16","RRD=4" is equ. what EthEnlargementPill does; hint: try negative memory clock and push memory timings even lower?
GeForce GTX 1080 | "FAW=16","RRD=4" is equ. what EthEnlargementPill does
GeForce GTX 1070 Ti |
GeForce GTX 1070 |
GeForce GTX 1060 6GB

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
    "CFG0_R0": 0,
    "CL": 24,
    "WL": 5,
    "RD_RCD": 26,
    "WR_RCD": 16,
    "CFG1_R0": 25,
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
    "DELAY0": 20,
    "CFG4_R0": 28,
    "ADR_MIN": 6,
    "CFG5_R0": 0,
    "WRCRC": 16,
    "CFG5_R1": 0,
    "OFFSET0": 39,
    "DELAY0_MSB": 0,
    "OFFSET1": 13,
    "OFFSET2": 7,
    "DELAY01": 12
  }
},
...
```