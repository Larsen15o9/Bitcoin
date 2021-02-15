### Error #102 Excavator.exe is missing
Most likely your Antivirus (AV) or Microsoft Defender has deleted it. Make sure to add exception for following files:
* excavator.exe
* NiceHashQuickMiner.exe
* nhqmservice.exe
* xmrig.exe

### Warning #103 Your PC does not have enough Virtual Memory set. 
This can cause mining failure. Increase your Virtual Memory size to at least 6000 MB times number of GPUs your PC has. Read [here](https://www.nicehash.com/blog/post/how-to-increase-virtual-memory-on-windows) how to increase Virtual Memory size.

### Excavator WARNING Device #X-X could not obtain power consumption!
Excavator is not capable of getting information about power consumption, therefore some functionality may not work (correctly). Fully reinstall your NVIDIA drivers to fix this issue.