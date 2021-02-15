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

Poor performance on GTX 1060, 1070 (Ti), 1080 (Ti).
You need to make sure, your card is running in P0 state. This can be achieved using some 3rd party tools as suggested in [this Reddit thread](https://www.reddit.com/r/RenderToken/comments/9w2rd9/how_to_use_maximum_p0_power_state_with_nvidia/).

Additionally, GTX 1080 and GTX 1080 Ti have GDDR5X memory which needs different memory timings for better performance. There is no publicly available code to do that, there are only closed source protected binaries of EthEnlargmentPill from unknown authors, which I do NOT suggest to use if you have any sensitive information.