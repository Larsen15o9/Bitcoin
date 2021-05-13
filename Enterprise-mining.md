## NiceHash QuickMiner with support for NVIDIA Quadro series and Tesla series

[Latest version of NiceHash QuickMiner](https://github.com/nicehash/NiceHashQuickMiner/releases) is bringing support for Enterprise class of NVIDIA video cards. For the first time in whole cryptocurrency mining history! If you have a powerful workstation or server full of Tesla cards. Now, when your power house is idle, you can **monetize idle time with just few clicks**, free of worries regarding security and safeness of shady miners. Read in general [why you should use QuickMiner and nothing else](https://github.com/nicehash/NiceHashQuickMiner/wiki/Why-NiceHash-QuickMiner) and what kind of [security mechanisms](https://github.com/nicehash/NiceHashQuickMiner/wiki/Security-Mechanisms) it uses **to keep you and your data safe**.

We have tested and created special [one click optimization](https://github.com/nicehash/NiceHashQuickMiner/wiki/One-click-Optimizations) profile called **Enterprise** for the following cards (more are coming!):

Device PCI ID | Device Name | Tested hashrate | Tested power consumption | Efficiency | Remarks
---|---|---|---|---|---
20F1 | Tesla A100 | ~170 MH/s | ~200 W | ~850 kH/J | Disable ECC for slightly better efficiency
2235 | A40 | ~83 MH/s | ~190 W | ~430 kH/J | Disable ECC, enable TCC
1EB8 | Tesla T4 | ~30 MH/s | ~65 W | ~460 kH/J | Disable ECC for extra ~5 MH/s
1B38 | Tesla P40 | ~37 MH/s | ~160 W | ~230 kH/J | Disable ECC for significant boost
1E30 | Quadro RTX 8000 | ~57 MH/s | ~160 W | ~350 kH/J | Need TCC and P0 state
1EB1 | Quadro RTX 4000 | ~37 MH/s | ~83 W | ~440 kH/J |
1C31 | Quadro P2200 | ~20 MH/s | ~65 W | ~300 kH/J | Enable TCC if getting memory issues
15F0 | Quadro GP100 | ~40 MH/s | ~150 W | ~260 kH/J | Enable TCC and P0 state

## What to do regarding NVIDIA Tesla?
- **Disable ECC** to improve efficiency and/or hashrate,
- can only change core clock limit - **Enterprise** optimization selects best settings to maximize efficiency.

## What to do regarding NVIDIA Quadro?
- If having low amount of VRAM (5GB), disable WDDM and enable TCC using `nvidia-smi` (without monitor plugged in),
- update to [Excavator Build 890](https://github.com/nicehash/NiceHashQuickMiner/releases/download/v0.5.1.6_RC/excavator_b890.zip) to fix 5GB memory limit bug,
- can manage fan and change core clock limit - **Enterprise** optimization selects best settings to maximize efficiency and optimize fan profile,
- try TCC with P0 state for CUDA workloads if possible (for now, set P0 for CUDA using [this useful tool](https://github.com/Orbmu2k/nvidiaProfileInspector)).

## Do you use Linux?
No problem! Just [virtualize QuickMiner](https://github.com/nicehash/NiceHashQuickMiner/wiki/Virtual-Mining). One click solutions for virtual mining are coming soon!