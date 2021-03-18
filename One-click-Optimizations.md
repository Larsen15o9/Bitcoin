# Optimize your GPU with one click!

When your rig appears in [Rig Manager](https://www.nicehash.com/my/mining/rigs) you can quickly optimize mining performance by clicking button `OPTIMIZE` and then choosing among three options:
- **Manual:** default mode, nothing is changed, NiceHash QuickMiner does not manage your GPU,
- **Lite:** mild optimization is applied and
- **Medium:** average optimization is applied.
![Optimisations](https://github.com/nicehash/NiceHashQuickMiner/blob/main/images/optimize_button.png?raw=true)

Following table explains for each GPU component what is happening. Do note that this table is very generalized and that each GPU might behave slightly differently.

Effect \ Optimization | **Manual** | **Lite** | **Medium** | **High**
---|------------|----------|------------|----
GPU Core Clock | Stock frequency | Very low frequency | Low frequency | _coming<br>soon_
GPU Vcore | Stock voltage | Stock voltage | Stock voltage | _coming<br>soon_
VRAM Clock | Stock frequency | Mildly increased frequency | Moderately increased frequency | _coming<br>soon_
Fan Speeds | GPU Default | Keep GPU* below 65 ℃ | Keep GPU* below 60 ℃ | _coming<br>soon_
Temperatures | Very high | Very low | Low | _coming<br>soon_
Power consumption | Very high | Very low | Low | _coming<br>soon_
Mining Speed | Low | Medium-High | High | _coming<br>soon_
**Efficiency** | **Poor** | **Good** | **Very good** | _coming<br>soon_

_* For RTX 3080 and RTX 3090 also keep VRAM Tjunction temperature below 95 ℃._

Optimization feature is only available for RTX 2000 series, RTX 3000 series, GTX 1660, GTX 1660 Ti, GTX 1660 Super, TITAN V and TITAN RTX. Do note that we are constantly trying to improve these optimizations which requires a lot of testing and performance measurements. Our numbers will surely improve in the near future to offer you even better performance and efficiency. To get latest optimization applied for your GPU, you only have to restart NiceHash QuickMiner. You can also view [latest raw data](https://github.com/nicehash/NiceHashQuickMiner/blob/main/optimize/data_003.json) that is being used. Medium optimization may not work for all cards. We are working on Lite optimization to be able to work for 99.9% of all video cards.

**WARNING:** Optimization applies overclock to your card which means that your card is running with clocks that were not set by NVIDIA. This means that your card may not be stable. It is strongly suggested to try Lite optimization first and test it for a day. If everything works okay, then try Medium. Also, do not enable Autostart with Windows before you finish performing optimizations. It can happen that you get caught in an endless restart loop because NiceHash QuickMiner applies overclocks at the start and can cause immediate crash of your system if clocks are too high for your system. In that case, unplugging internet connection for the boot time may help because Excavator cannot mine until it gets data from the servers.

Additional good-to-know:
- Do not use MSI Afterburner. NiceHash QuickMiner has everything you need. MSI Afterburner can only mess with QuickMiner settings and results can be very unpredictable then.
- Before using Optimize button, make sure you **did not set Force P0 for Cuda**. Memory overclocks will most likely be too high in that case and crash your PC.
- Optimize was designed as an All-In-One solution. This means that you do **not need any** other tool/program but just NVIDIA drivers and NiceHash QuickMiner after you setup a freshly installed Windows 10.
- Do not use OCTune or any other overclocking tool AND OPTIMIZE at the same time. If you have manual overclock settings (OCTune, MSI Afterburner) then choose OPTIMIZE - Manual.

## What can I expect from optimizations?
We have gathered all data together and here is what you get in terms of speed, temperatures and consumption for some known popular cards:
**Video Card - Optimization** | **Speed** | **Power consumption** | **Efficiency** | **Temperature**
---|------------|----------|------------|----
GeForce RTX 3090 - Medium | 116-117 MH/s | 270-280 W | 415-435 kH/J | GPU Core: max 60 ℃<br>VRAM: max 95 ℃
GeForce RTX 3090 - Lite | 100-102 MH/s | 250-260 W | 385-410 kH/J | GPU Core: max 64 ℃<br>VRAM: max 95 ℃
GeForce RTX 3080 - Medium | 96 MH/s | 220-240 W | 400-435 kH/J | GPU Core: max 60 ℃<br>VRAM: max 95 ℃
GeForce RTX 3080 - Lite | 90 MH/s | 200-220 W | 410-450 kH/J | GPU Core: max 64 ℃<br>VRAM: max 95 ℃
GeForce RTX 3070 - Medium | 60-61 MH/s | 110-130 W | 460-550 kH/J | GPU Core: max 60 ℃
GeForce RTX 3070 - Lite | 58 MH/s | 105-120 W | 480-550 kH/J | GPU Core: max 64 ℃
GeForce RTX 3060 Ti - Medium | 60-61 MH/s | 110-130 W | 460-550 kH/J | GPU Core: max 60 ℃
GeForce RTX 3060 Ti - Lite | 58 MH/s | 105-120 W | 480-550 kH/J | GPU Core: max 64 ℃
GeForce GTX 1660 SUPER - Medium | 31 MH/s | 70-80 W | 390-440 kH/J | GPU Core: max 60 ℃
GeForce GTX 1660 SUPER - Lite | 30 MH/s | 65-75 W | 400-460 kH/J | GPU Core: max 64 ℃
GeForce GTX 1660 - Medium | 25 MH/s | 46-56 W | 440-540 kH/J | GPU Core: max 60 ℃
GeForce GTX 1660 - Lite | 24 MH/s | 44-54 W | 440-540 kH/J | GPU Core: max 64 ℃

If you cannot reach speeds listed above, then consider [answer to the following question explained here](https://github.com/nicehash/NiceHashQuickMiner/wiki/FAQ#faq08).