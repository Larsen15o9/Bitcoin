**NiceHash QuickMiner is using following security mechanisms to keep you, your PC and your data safe and secure.**

### Verified and audited code from known source
Every piece of code, library or linked library is either:
* developed by NiceHash developers,
* available publicly as open source (under certain license that permits usage in our distribution model),
* trusted by Microsoft (for example, NVIDIA drivers) or
* created long time ago, used by many applications over past years and thus considered safe by many (if you enable CPU mining, a special driver is dropped and launched - _WinRing0x64.sys_ - we do not have source code for it, but the driver is signed and ~13 years old so we do not believe it is harmful in any way).

### Publicly available hash checksums for all released ZIP packages
Every release made by NiceHash has a known SHA1 and SHA256 hash, so you can verify whether you have downloaded authentic ZIP package and that no files were modified between GitHub and your PC. More about it is available [here](https://github.com/nicehash/NiceHashQuickMiner/tree/main/checksums).

### Exclusive HTTPS connections to get/send data
Any connection established by NiceHash QuickMiner or Excavator to any service is always forced HTTPS. Non HTTPS or servers that do not support modern cryptographic standards are refused. This is very important as it prevents any kind of MITM (man-in-the-middle) attacks and your hashrate cannot be redirected to another server or potential attackers cannot offer you a malicious update. 

### Executables signed with EV Code Signing Certificate
[More about EV Code Signing Certificate](https://www.digicert.com/signing/code-signing-certificates). For practical reasons, only STABLE releases are fully signed. Installer is always signed. A signed installer gives you confidence that the software you are installing is actually from NiceHash and not potential attackers. Authenticity of install and update packages is guaranteed by the security feature explained in the next step.

### Authentic download/update mechanism using N/M signatures
When new software is downloaded, there can always be a problem of trust - an existing software must know whether it can trust new software that is being downloaded and executed. We use own developed N/M signatures for this purpose. There are 3 valid signatures needed for any update to be considered authentic. This security feature guarantees you that potential attackers cannot push you a malicious update even if they took control of the whole NiceHash'es GitHub repository. This security feature is available from version 0.4.5.3.

### Limited CORS and Authorization token
From version 0.4.5.0, Excavator.exe does not allow [CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS) anymore. This means that a potential attacker, if you visit a malicious website, cannot execute command to mine to his own Mining Address instead of yours. Extra layer of security is provided by using _Authorization token_ for any write-type of command.