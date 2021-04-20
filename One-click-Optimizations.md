# Optimize your GPU with one click!

When your rig appears in [Rig Manager](https://www.nicehash.com/my/mining/rigs) you can quickly optimize mining performance by clicking button `OPTIMIZE` and then choosing among following options:
- **Manual:** default mode, nothing is changed, NiceHash QuickMiner does not manage your GPU,
- **Lite:** mild optimization is applied,
- **Medium:** average optimization is applied,
- **High:** high optimization is applied and
- **Efficient:** efficient optimization is applied.

![Optimisations](https://github.com/nicehash/NiceHashQuickMiner/blob/main/images/optimize_button.png?raw=true)

Following table explains for each GPU component what is happening. Do note that this table is very generalized and that each GPU might behave slightly differently.

Effect | **Manual** | **Lite** | **Medium** | **High** | **Efficient**
---|------------|----------|------------|----|----
GPU Core Clock | Stock frequency | Low frequency | Medium frequency | Medium-High frequency | Low-Medium frequency
GPU Vcore | Stock voltage | Stock voltage | Stock voltage | Stock voltage | **Undervolted**
VRAM Clock | Stock frequency | Mildly increased frequency | Moderately increased frequency | High frequency | Moderately increased frequency
VRAM Timings | Stock timings | Stock timings | Stock timings | Stock timings | **Modified**
Fan Speeds | GPU Default | Keep GPU* below 65 ℃ | Keep GPU* below 60 ℃ | Keep GPU* below 60 ℃ | Keep GPU* below 65 ℃
Temperatures | Very high | Low | Low | Low | Low
Power consumption | Very high | Very low | Low | Low-Moderate | Very low
Mining Speed | Low | Medium | Medium-High | High | Medium-High 
**Efficiency** | **Poor** | **Good** | **Good** | **Good** | **Excellent**

_* For RTX 3080 and RTX 3090 also keep VRAM Tjunction temperature below 95 ℃._

With version 0.4.4.0 **Efficient OPTIMIZATION** is available for certain video cards. This optimization gives you almost the highest possible efficiency using various tuning mechanisms including adjusting memory timings and setting under-voltages. It may not work on all cards, but we are trying to set parameters to fit most of the cards. **Efficient OPTIMIZATION** will be first available for Pascal (1000 series) and Volta cards. Later we will try to offer good profiles for Turing (2000 series) and Ampere (3000 series) based cards.

Do note that we are constantly trying to improve these optimizations which requires a lot of testing and performance measurements. Our numbers will surely improve in the near future to offer you even better performance and efficiency. To get latest optimization applied for your GPU, you only have to restart NiceHash QuickMiner. You can also view [latest raw data](https://github.com/nicehash/NiceHashQuickMiner/blob/main/optimize/data_005.json) that is being used. Medium, High and Efficient optimizations may not work for all cards. We are working on Lite optimization to be able to work for 99.9% of all video cards.

**WARNING:** Optimization applies overclock to your card which means that your card is running with clocks that were not set by NVIDIA. This means that your card may not be stable. It is strongly suggested to try Lite optimization first and test it for a day. If everything works okay, then try Medium. Also, do not enable Autostart with Windows before you finish performing optimizations. It can happen that you get caught in an endless restart loop because NiceHash QuickMiner applies overclocks at the start and can cause immediate crash of your system if clocks are too high for your system. In that case, unplugging internet connection for the boot time may help because optimization data cannot be downloaded and Excavator cannot mine until it gets data from the servers.

Additional good-to-know:
- Do not use MSI Afterburner. NiceHash QuickMiner has everything you need. MSI Afterburner can only mess with QuickMiner settings and results can be very unpredictable then.
- Before using Optimize button, make sure you **did not set Force P0 for Cuda**. Memory overclocks will most likely be too high in that case and crash your PC.
- Optimize was designed as an All-In-One solution. This means that you do **not need any** other tool/program but just NVIDIA drivers and NiceHash QuickMiner after you setup a freshly installed Windows 10.
- Do not use OCTune or any other overclocking tool AND OPTIMIZE at the same time. If you have manual overclock settings (OCTune, MSI Afterburner) then choose OPTIMIZE - Manual.

## What can I expect from optimizations?
We have gathered all data together and here is what you get in terms of speed, temperatures and consumption for some known popular cards:
**Video Card - Optimization** | **Speed** | **Power consumption** | **Efficiency** | **Temperature**
---|------------|----------|------------|----
GeForce RTX 3090 - Extreme<br>**Only for water cooled GPU!** | 125 MH/s | 290-310 W | 405-435 kH/J | GPU Core: max 50 ℃<br>VRAM: max 80 ℃
GeForce RTX 3090 - High | 121-122 MH/s | 280-290 W | 415-435 kH/J | GPU Core: max 60 ℃<br>VRAM: max 95 ℃
GeForce RTX 3090 - Medium | 116-117 MH/s | 270-280 W | 415-435 kH/J | GPU Core: max 60 ℃<br>VRAM: max 95 ℃
GeForce RTX 3090 - Lite | 100-102 MH/s | 250-260 W | 385-410 kH/J | GPU Core: max 64 ℃<br>VRAM: max 95 ℃
GeForce RTX 3080 - Medium | 96 MH/s | 210-230 W | 420-455 kH/J | GPU Core: max 60 ℃<br>VRAM: max 95 ℃
GeForce RTX 3080 - Lite | 91 MH/s | 195-215 W | 425-460 kH/J | GPU Core: max 64 ℃<br>VRAM: max 95 ℃
GeForce RTX 3070 - Medium | 60-61 MH/s | 110-130 W | 460-550 kH/J | GPU Core: max 60 ℃
GeForce RTX 3070 - Lite | 58 MH/s | 105-120 W | 480-550 kH/J | GPU Core: max 64 ℃
GeForce RTX 3060 Ti - Medium | 60-61 MH/s | 110-130 W | 460-550 kH/J | GPU Core: max 60 ℃
GeForce RTX 3060 Ti - Lite | 58 MH/s | 105-120 W | 480-550 kH/J | GPU Core: max 64 ℃
TITAN RTX - Medium | 63 MH/s | 150-160 W | 390-420 kH/J | GPU Core: max 60 ℃<br>VRAM: max 75 ℃
TITAN RTX - Lite | 58 MH/s | 140-150 W | 385-415 kH/J | GPU Core: max 64 ℃<br>VRAM: max 75 ℃
GeForce GTX 1660 SUPER - Medium | 31 MH/s | 70-80 W | 390-440 kH/J | GPU Core: max 60 ℃
GeForce GTX 1660 SUPER - Lite | 30 MH/s | 65-75 W | 400-460 kH/J | GPU Core: max 64 ℃
GeForce GTX 1660 - Medium | 25 MH/s | 46-56 W | 440-540 kH/J | GPU Core: max 60 ℃
GeForce GTX 1660 - Lite | 24 MH/s | 44-54 W | 440-540 kH/J | GPU Core: max 64 ℃


From version 0.4.3.0 Pascal cards are also supported. This is currently experimental and we are still collecting data. So far the results are following:
**Video Card - Optimization** | **Speed** | **Power consumption** | **Efficiency** | **Temperature**
---|------------|----------|------------|----
GeForce GTX 1080 Ti - High | 45-46 MH/s | 210 W |  | GPU Core: max 60 ℃
GeForce GTX 1080 Ti - Medium | 43-45 MH/s | 210 W | 205-215 kH/J | GPU Core: max 60 ℃
GeForce GTX 1080 Ti - Lite | 37 MH/s | 160 W | 230 kH/J | GPU Core: max 64 ℃
GeForce GTX 1080 - High | 33-34 MH/s | 140 W |  | GPU Core: max 60 ℃
GeForce GTX 1080 - Medium | 30-31 MH/s | 130 W | 230-240 kH/J | GPU Core: max 60 ℃
GeForce GTX 1080 - Lite | 25 MH/s | 100 W | 240 kH/J | GPU Core: max 64 ℃
GeForce GTX 1070 Ti - Medium | 31 MH/s | 125 W | 250 kH/J | GPU Core: max 60 ℃
GeForce GTX 1070 Ti - Lite | 29 MH/s | 110 W | 260 kH/J | GPU Core: max 64 ℃
GeForce GTX 1070 - High | 28 MH/s | 120 W |  | GPU Core: max 60 ℃
GeForce GTX 1070 - Medium | 27 MH/s | 110 W |  | GPU Core: max 60 ℃
GeForce GTX 1070 - Lite | 26 MH/s | 100 W |  | GPU Core: max 64 ℃
GeForce GTX 1060 6GB - High | 25 MH/s | 100 W |  | GPU Core: max 60 ℃
GeForce GTX 1060 6GB - Medium | 24 MH/s | 90 W | 260 kH/J | GPU Core: max 60 ℃
GeForce GTX 1060 6GB - Lite | 22 MH/s | 80 W | 270 kH/J | GPU Core: max 64 ℃

If you cannot reach speeds listed above, then consider [answer to the following question explained here](https://github.com/nicehash/NiceHashQuickMiner/wiki/FAQ#faq08).


## Is it possible to slightly modify OPTIMIZATION profiles?
From version 0.4.3.0 this is possible. Steps are following:
1. Download appropriate Optimization data file (currently this is [v6](https://github.com/nicehash/NiceHashQuickMiner/blob/main/optimize/data_006.json)) and save it somewhere on your hard drive. Let's assume location we save it into is `D:\nhqm\optimize\data_006.json`.
2. In config file _nhqm.conf_ modify `"optimizeProfilesCustomDataURL" : null` to `"optimizeProfilesCustomDataURL" : "D:\\nhqm\\optimize\\data_006.json"`. Be aware of **the double backslashes** - if you use single, the whole config file gets corrupted and new one is generated. Here you can also use your own HTTPS URL to replace the GitHub's default one. If set to null, then default hardcoded URL is used which is regularly maintained by NiceHash team to offer best possible performance and reliability for most of the cards.
3. Modify `D:\nhqm\optimize\data_006.json` file. From version 3, property names are much shortened, but are still the same as used in [version 2](https://github.com/nicehash/NiceHashQuickMiner/blob/main/optimize/data_002.json). Some can be figured by looking at examples. `pt` (profile type) 1 has several extra properties:
  * `dcc` is delta core clock,
  * `pl` is power limit in Watts and
  * `mt` is memory timings array.

`mcc` (max core clock) is not being used in profile type 1. Profile type 1 are used by GPUs from Pascal series (1000 without 1660). Setting max core clock is not possible for Pascal cards.

4. Keep in mind that you should regularly check official OPTIMIZE data so you do not get left behind. Also, with any major change to this part of the subsystem, a new version gets used which means that your locally saved file would not work anymore. Then you have to either change `"optimizeProfilesCustomDataURL"` back to `null` or download new version OPTIMIZE data and modify new one.