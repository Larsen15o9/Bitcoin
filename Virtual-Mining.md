# Virtual Mining

NVIDIA has added support for GeForce series cards to be fully supported in virtualized environment using PCI-e pass-through method (no more code error 43). Support is available with the latest drivers [465.89](https://www.nvidia.com/download/driverResults.aspx/172060/en-us). We have spent some time and tested out various cards (Pascal, Turing, Ampere) and we can confirm that cryptomining in virtual environment now finally works. With some proper tweaking, the stability is good and speeds are identical to the ones possible to achieve native way. Because this is pass-through method, guest OS has complete control over GPU which means also complete access to tuning parameters such as clocks, voltages and memory timings.

Following is an example of two virtual guest Windows 10 machines running QuickMiner, one having 3 cards and another one having 7 cards. All 10 cards are actually physically connected to the same rig. Host OS is **vmware ESXi**. We are confident this method will work with various Linux-Host virtualization scenarios.
![vmining](https://github.com/nicehash/NiceHashQuickMiner/blob/main/images/virtualmining.png?raw=true)

## What does this mean? How can it improve mining?
**"Virtual Mining"** brings following improvements, shortly described for better understanding.

### 1. Increased security
Now it is possible to improve your safety while mining several fold, because the mining software can be contained inside virtual OS. There is unfortunately no easy one-click solution and even though, we would like to make one, we do not believe this is possible due to various reasons (including legal). But for hard-core security freaks who do not trust anything at all, this brings a possibility to finally be able to execute mining software that can utilize their GPU.

### 2. Improved accessibility of mining software
Linux users can now run Windows-only mining software such as QuickMiner without any performance penalties.

### 3. Possibility for increased reliability
NVIDIA drivers are made in a way that one failure of any card makes failure of all cards. Using virtual isolation, each card has own driver and if certain card crashes, others are not affected. This can bring overall better reliability which in turn brings more income for miners.

### 4. New management possibilities
Larger rigs can be split into smaller ones thus bringing new opportunities for hashrental and similar businesses. A layer of virtualization aids freely with extra layer of management which makes necessity for tools such as TeamViewer obsolete. Needed video card for management purposes is virtual thus removing all performance penalties incurred on GPU for video encoding.

## "Virtual Mining" and NiceHash
We will shortly provide you with guides how to establish QuickMiner for various virtualization environments. Because Linux version of NVIDIA drivers does not have NVAPI, which provides substantial help when it comes to managing and tweaking NVIDIA video cards, we believe that a combination of Linux (Host) - Windows (Guest) mining system is needed that could eventually prevail and later, if NVAPI is introduced to Linux, a Linux - Linux mining system could be greatly superior compared to current mining OS versions used by miners.
