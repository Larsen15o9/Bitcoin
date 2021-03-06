Following video cards are officially tested and fully supported:
Device Name | Possible best hashrate* | Possible best Efficiency* | Remarks
-------|----------|------------|-----
NVIDIA GeForce GTX 1060 6GB | 24 MH/s | - | Force CUDA P0 state for max performance
NVIDIA GeForce GTX 1070 | - | - | Force CUDA P0 state for max performance
NVIDIA GeForce GTX 1070 Ti | 32 MH/s | - | Force CUDA P0 state for max performance
NVIDIA GeForce GTX 1080 | - | - | -
NVIDIA GeForce GTX 1080 Ti | 38 MH/s | - | -
NVIDIA TITAN Xp | - | - | -
NVIDIA TITAN V | 75 MH/s | 580 kH/J | - | Max clock 930, 125 W
NVIDIA GeForce GTX 1660 | 25 MH/s | 530 kH/J | Max clock 1230, Mem +600, 25 MH/s @ 48 W
NVIDIA GeForce GTX 1660 Super | 32 MH/s | 410 kH/J | Set mem -505!
NVIDIA GeForce GTX 1660 Ti | 32 MH/s | 475 kH/J | Mem +900, max clock 900
NVIDIA GeForce RTX 2060 | 33 MH/s | 390 kH/J | Mem +900, max clock ~1050
NVIDIA GeForce RTX 2060 Super | - | - | Mem +900, max clock ~1050
NVIDIA GeForce RTX 2070 | 44 MH/s | 410 kH/J | Mem +900, max clock ~1050
NVIDIA GeForce RTX 2070 Super | 44 MH/s | 430 kH/J | Mem +900, max clock ~1050
NVIDIA GeForce RTX 2080 | 44 MH/s | 410 kH/J | Mem +900, max clock ~1050
NVIDIA GeForce RTX 2080 Super | 44 MH/s | - | Mem +900, max clock ~1050
NVIDIA GeForce RTX 2080 Ti | 63 MH/s | 420 kH/J | Mem +1000, max clock ~1050
NVIDIA TITAN RTX | 66 MH/s| 430 kH/J | Mem +1100, max clock ~1000
NVIDIA GeForce RTX 3060 | 26 MH/s | 350 kH/J | Crippled by NVIDIA
NVIDIA GeForce RTX 3060 Ti | 63 MH/s | 520 kH/J | 62-64 MH/s - depends on chip
NVIDIA GeForce RTX 3070 | 63 MH/s | 525 kH/J | 62-64 MH/s - depends on chip
NVIDIA GeForce RTX 3080 | 101 MH/s | 460 kH/J | Keep GDDR6X cool for max eff.
NVIDIA GeForce RTX 3090 | 126 MH/s | 425 kH/J | Keep GDDR6X cool for max eff.

_* Best possible hashrate and best possible efficiency heavily depends on quality of the chip. Some chips can run at lower voltage and some chips needs higher voltage. The end result is that some chips can reach higher speeds with lower power consumption thus yielding better efficiency. Mentioned results are according to our internal tests withs limited amount of video cards._

Note the above models are **only** desktop variants. Notebook variants are not tested and we do not recommend using notebook video cards for mining due to extreme heat generated. If the video card is not on the list above, it may still (partially) work. Some Quadro and Tesla versions may work. We are working on bringing full compatibility to these models as well.

Additionally to the above video cards, if your PC has capable CPU, you can enable CPU mining. Following CPUs are supported:
* All Intel CPUs with AVX2 support
* All AMD CPUs with AVX2 support

**NOTE: CPU mining is only addition to GPU mining. You cannot use QuickMiner to only do CPU mining without GPU mining - it does not work. Please use [NiceHash Miner](https://github.com/nicehash/NiceHashMiner) if you plan to do only CPU mining.**