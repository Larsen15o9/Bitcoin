## What is MSI?
[Message Signaled Interrupts](https://en.wikipedia.org/wiki/Message_Signaled_Interrupts) is a method of CPU-GPU communication. Wiki states that:
> ... While more complex to implement in a device, message signalled interrupts have some significant advantages over pin-based out-of-band interrupt signalling.

When activating MSI, you can actually notice that your GPU will is more stable. Especially if your GPU crashes here and there due to high OC values, crash will be easily recoverable without PC restart and other GPUs will not be so drastically affected. Without MSI enabled, a crash of a single GPU usually results in a blue screen of entire OS thus reboot of the PC.

## Great, how can I use it?
To be able to use MSI, you need to have hardware (GPU, motherboard) and software (OS, drivers) that supports it. All QuickMiner supported hardware supports MSI, Windows 10 x64 supports MSI and NVIDIA drivers supports MSI. But for some reason, **installation of NVIDIA drivers sets all Pascal, Volta and Turing based cards to NOT use MSI thus manual activation is needed**. This can be done [modifying registry manually](https://forums.guru3d.com/threads/windows-line-based-vs-message-signaled-based-interrupts-msi-tool.378044/) or using [latest version of NiceHash QuickMiner](https://github.com/nicehash/NiceHashQuickMiner/releases). NiceHash QuickMiner will also detect whether MSI optimization is possible and throw you **warning #104** if you should apply it.

You can apply MSI Interrupts easily with one click of a button as shown in the picture below:

![msiapply](https://github.com/nicehash/NiceHashQuickMiner/blob/main/images/applymsi.png?raw=true)

Do not forget to reboot your PC/Rig after. Also, each time you install or update drivers, you will have to apply MSI optimization, because installation of drivers override your manual settings. 

## Is it mandatory to apply it?
No, you do not have to apply it. On some systems with certain combination of hardware and software, it may cause issues. We are just investigating this. The reason is probably in buggy implementation in NVIDIA's either drivers or hardware hence reason why MSI is disabled by default. When we know more, we will update this page.
