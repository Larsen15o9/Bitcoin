## QuickMiner: Smart Fan 
Smart Fan's Target GPU&VRAM mode has proven to be very useful and reliable feature of QuickMiner, used by many. Even though it is nearly perfect, it still lacks ability to take more drastic measures when temperature is too high. Besides, many do not want to run fans at 100% speed as that wears them out quicker thus shortens fans' lifespan. New fan mode called **Target plus decrease MCC** resolves these issues.

## Smart Fan mode: Target plus decrease MCC
Target plus decrease MCC fan mode (available with version 0.5.1.0+) is an intelligent Smart Fan mode which works similar as Target Core&VRAM (mode 3) with upgrade - when max set fan speed is reached and temperature is still over target, MCC (max core clock) is being reduced thus reducing power output of the GPU which most likely reduces temperature. The newest Smart Fan mode takes in one more parameter - max fan speed which is identical to Smart Fan's advanced parameters `override_level_max` (default = -1 = use GPU's default max level = in most cases this is 100%). This fan mode enables you to really take control of the temperatures and make sure to keep them in check with drastic measures (reducing clocks, load and power) if needed. It is NOT available for Pascal architecture, but fully supported for Volta, Turing and Ampere, because prior enabling it, alternative OC needs to be set with defined MCC (core clock limit).

## How to use it

**IMPORTANT: This mode works only for GTX 1660 (Ti/SUPER), TITAN V, TITAN RTX and RTX series. It does not work for GTX 1060, 1070, 1080 or 1080 Ti cards.**

1. Download, unzip, install and configure [latest version](https://github.com/nicehash/NiceHashQuickMiner/releases).
2. In Rig Manager **set Manual optimization profile**. 
3. Open OCTune and select your GPU (_Single selected device_).
4. Use **Alternative method for overclocking** to set _Core clock limit_ and _Memory clock (absolute)_ for your GPU.
5. Under **Fan management** set _Fan mode_ to **Target plus decrease MCC**.
6. Set target GPU and VRAM temperatures just like adjusting for Target mode.
7. Optionally, you can set max fan speed (or level, in %). Set to -1 if you wish to use GPU's default (in most cases that is 100%). If you wish to have fans at max 60%, then enter `60` under _Max fan speed_.
8. Click button `Single`.
9. Optionally, if you wish to keep this configuration every time you start QuickMiner, click the green button `Save current configuration`.

Your GPU will work in following way: when GPU or VRAM temperature is breached, fan speed is increased. If fan speed is already at max, then max core clock (or core clock limit) is decreased in steps 15 at a time until temperature drops to target level. If temperature drops under target level, then max core clock will be increased until reaching your original adjusted value when setting OC. If even then temperature is still below target, fan speed is going to be decreased until temperature matches target value.

This mode is therefore great if you value your GPU greatly and you do not wish it to exceed VRAM temperatures too much (certain RTX 3080 and 3090 models with awful VRAM cooling). If you would rather sacrifice hashing speed instead of having high temperature (eg. of VRAM), then this new mode is perfect for you.