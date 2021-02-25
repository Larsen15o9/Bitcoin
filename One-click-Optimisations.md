# Optimize your GPU with one click!

When your rig appears in [Rig Manager](https://www.nicehash.com/my/mining/rigs) you can quickly optimize mining performance by clicking button `OPTIMIZE` and then choosing among three options:
- **Manual:** default mode, nothing is changed, NiceHash QuickMiner does not manage your GPU,
- **Lite:** mild optimisation is applied and
- **Medium:** average optimisation is applied.
![Optimisations](https://github.com/nicehash/NiceHashQuickMiner/blob/main/images/optimize_button.png?raw=true)

Following table explains for each GPU component what is happening. Do note that this table is very generalized and that each GPU might behave slightly differently.

Effect \ Optimisation | **Manual** | **Lite** | **Medium** | **High**
---|------------|----------|------------|----
GPU Core Clock | Stock frequency | Very low frequency | Low frequency | _coming<br>soon_
VRAM Clock | Stock frequency | Mildly increased frequency | Moderately increased frequency | _coming<br>soon_
Fan Speeds | GPU Default | Keep GPU* below 60 ℃ | Keep GPU* below 60 ℃ | _coming<br>soon_
Temperatures | Very high | Very low | Low | _coming<br>soon_
Power consumption | Very high | Very low | Low | _coming<br>soon_
Mining Speed | Low | Medium-High | High | _coming<br>soon_
**Efficiency** | **Poor** | **Good** | **Very good** | _coming<br>soon_

_* For RTX 3080 and RTX 3090 also keep VRAM Tjunction temperature below 95 ℃._

Optimisation feature is only available for RTX 2000 series, RTX 3000 series, GTX 1660, GTX 1660 Ti, GTX 1660 Super and TITAN V. Do note that we are constantly trying to improve these optimizations which requires a lot of testing and performance measurements. Our numbers will surely improve in the near future to offer you even better performance and efficiency. To get latest optimisation applied for your GPU, you only have to restart NiceHash QuickMiner. You can also view [latest raw data](https://github.com/nicehash/NiceHashQuickMiner/blob/main/optimize/data_002.json) that is being used. Medium optimisation may not work for all cards. We are working on Lite optimisation to be able to work for 99.9% of all video cards.

**WARNING:** Optimisation applies overclock to your card which means that your card is running with clocks that were not set by NVIDIA. This means that your card may not be stable. It is strongly suggested to try Lite optimisation first and test it for a day. If everything works okay, then try Medium. Also, do not enable Autostart with Windows before you finish performing optimisations. It can happen that you get caught in an endless restart loop because NiceHash QuickMiner applies overclocks at start and can cause immediate crash of your system if clocks are too high for your system. In that case, unplugging internet connection for the boot time may help because Excavator cannot mine until it gets data from the servers.

Additional good-to-know:
- Do not use MSI Afterburner. NiceHash QuickMiner has everything you need. MSI Afterburner can only mess with QuickMiner settings and results can be very unpredictable then.
- Before using Optimize button, make sure you **did not set Force P0 for Cuda**. Memory overclocks will most likely be too high in that case and crash your PC.
- Optimize was designed as an All-In-One solution. This means that you do **not need any** other tool/program but just NVIDIA drivers and NiceHash QuickMiner after you setup a freshly installed Windows 10.