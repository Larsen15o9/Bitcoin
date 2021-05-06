## NiceHash QuickMiner with support for NVIDIA Quadro series and Tesla series

Device PCI ID | Device Name | Tested hashrate | Tested power consumption | Efficiency | Remarks
---|---|---|---|---|---
20F1 | Tesla A100 | ~170 MH/s | ~200 W | 850 kH/J | Disable ECC for slightly better efficiency
1EB8 | Tesla T4 | ~30 MH/s | ~65 W | 460 kH/J | Disable ECC for extra ~5 MH/s
1EB1 | Quadro RTX 4000 | ~37 MH/s | ~83 W | 440 kH/J |
1C31 | Quadro P2200 | ~20 MH/s | ~65 W | 300 kH/J | **Enable TCC** if getting memory issues

## What to do regarding NVIDIA Tesla?
- **Disable ECC** to improve efficiency and/or hashrate,
- Can only change core clock limit - **Enterprise** optimization selects best settings to maximize efficiency.

## What to do regarding NVIDIA Quadro?
- If having low amount of VRAM (5GB), disable WDDM and enable TCC using `nvidia-smi` (without monitor plugged in),
- Can manage fan and change core clock limit - **Enterprise** optimization selects best settings to maximize efficiency and optimize fan profile.