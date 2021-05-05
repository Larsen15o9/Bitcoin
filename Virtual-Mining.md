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


# Linux & QuickMiner

**WARNING: Incomplete instructions! Work in progress...**


### BIOS preparation - TODO
* Enable VT-d (Intel) or IOMMU (AMD)
* Enable PCI Express Access Control Services (ACS) - if available
* More: https://kb.vmware.com/s/article/2142307


### Host OS preparation
1. Install [Bare Metal Hypervisor: VMware ESXi](https://www.vmware.com/products/esxi-and-esx.html) on your rig. This Host OS has 90-day free trial.
2. From another device remotely access WMware ESXi Web portal. Login with `root` as user name and password you used during installation of the Hypervisor in previous step.
3. Enter `Maintenance mode`: _Navigator_ -> _Host_ -> _Actions_ -> _Enter maintenance mode_
4. Set High performance power policy: _Navigator_ -> _Host_ -> _Manage_ -> _Hardware_ -> _Power Management_ -> _Change policy_ -> _High performance_
5. Configure selected NVIDIA GeForce/TITAN video cards. Under _Navigator_ -> _Host_ -> _Manage_ -> _Hardware_ -> _PCI Devices_ find GeForce/TITAN video cards that you would like to use for mining. Select and click _Toggle passthrough_ so that _Passthrough_ for selected video card is **Active**. You may have some issues here (unable to set **Active** or message **Requires Reboot** appearing). If that is the case, under _Navigator_ -> _Host_ -> _Manage_ -> _System_ -> _Advanced settings_ find key `VMkernel.Boot.disableACSCheck` and set it to `true`. Reboot and you shall not have issues activating passthrough anymore.


### Guest OS preparation
6. Get and install Windows 10 x64 as virtual machine in VMware ESXi. If you do not have Windows 10 x64, you can use 90-day free trial from [here](https://developer.microsoft.com/en-us/microsoft-edge/tools/vms/). If you are using your own Windows 10 installation, skip following steps and go directly to point 13.
7. Select appropriate download - Virtual Machine: _MSEdge on Win10_ and VM platform: _VMware_. Download .zip file and extract it.
8. Create New virtual machine - choose _Deploy a virtual machine from an OVF or OVA file_. Use **.ovf** and **.vmdk** files out of downloaded .zip file. Wait until new virtual machine is fully deployed.
9. Edit virtual machine; configure CPU, Memory (set **Reserve all guest memory**), and increase Hard disk size to at least 100 GB.
10. Power on virtual machine and let it install VMware Tools. It is suggested to remove password **Passw0rd!** and use blank thus account is logged in directly when Windows boot.
11. In guest Windows OS open cmd.exe as Administrator and execute: `MBR2GPT.exe /convert /allowfullos`
12. Power off virtual machine and change _Edit_ -> VM Options_ -> _Boot Options_ -> _Firmware_ from `BIOS` to `EFI`.

13. In guest Windows OS [increase pagefile size](https://www.nicehash.com/blog/post/how-to-increase-virtual-memory-on-windows), set high performance profile and other tweaks to improve performance and stability.
14. Install latest Windows updates and adjust update related settings.


### Guest OS configuration
15. According to [this article](https://kb.vmware.com/s/article/2142307), add two **Configuration Parameters** to the virtual machine:
> pciPassthru.use64bitMMIO TRUE

and

> pciPassthru.64bitMMIOSizeGB 32

16. Add selected video cards to the virtual machine by clicking on **Add other device**, choosing **PCI device** and then selecting appropriate video card in the combobox list.
17. Configuration of virtual machine is complete. Additionally you may configure whether virtual machine is automatically started with the Host.


### Driver installation and final tweaks
20. In guest Windows OS, download and install latest non-DCH NVIDIA drivers (at least version [465.89](https://www.nvidia.com/download/driverResults.aspx/172060/en-us)).
21. **Following step is very important to improve stability of your virtual miner. Without this tweak, your mining rig may not be stable even 5 minutes!** You need to [set Message Signaled-Based Interrupts](https://forums.guru3d.com/threads/windows-line-based-vs-message-signaled-based-interrupts-msi-tool.378044/) (MSI) for your video cards. You can do it manually changing Windows Registry or using 3rd party tool provided by the author of the article. After modifying Registry values, make the final reboot of the virtual machine. Your virtual miner is now ready for QuickMiner.
**Each driver update will reset this optimization. It is good to periodically check this value. QuickMiner v0.5.0.0+ will have tools for easy MSI checkup and management.**
22. Download, install, configure and mine using [latest version of NiceHash QuickMiner](https://github.com/nicehash/NiceHashQuickMiner/releases) which is fully supported and compatible with virtualization-techniques.