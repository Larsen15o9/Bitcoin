### From version 0.4.2.0 - ability to modify certain memory timings

Example of commands.json file which modifies timings for GPU0:
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

Name | Known values | Remarks
-----|--------------|----------
__MT0 | 24, 20, 16 | GDDR5X has this value 24 or 20 (1080 Ti or 1080). Set to 16 for better performance.
__MT1 | 6, 5, 4 | GDDR5X has this value 6 or 5 (1080 Ti or 1080). Set to 4 for better performance. Looks like being 1/4 of __MT0.