### 1. Choose your service location to improve your latency and reduce number of stale shares

Open nhqm.conf (NiceHash QuickMiner right click notification icon and choose `Settings` -> `Edit config file`) and modify `"serviceLocation"`. Following locations are possible:
* Europe (Belgium): `0`,
* USA (California): `1`.

In the near future, more locations will be possible to choose from. After saving the config file, your mining location will be updated almost instantly. Observe latencies from accepted shares in Excavator console.

![Latency picture](https://github.com/nicehash/NiceHashQuickMiner/blob/main/images/latency.png?raw=true)

The numbers marked with red squares must be as low as possible. Experiment with serviceLocation until you get the best result.

### 2. Change your worker name

If you have more mining PCs, you can set name for each one. You can do this online through [Rig Manager](https://www.nicehash.com/my/mining/rigs) or locally through config. Open nhqm.conf (NiceHash QuickMiner right click notification icon and choose `Settings` -> `Edit config file`) and modify `"workerName"`. Name should only contain alphanumeric characters of English alphabet and max length is 15 characters.

### 3. Define what happens when something goes wrong

Mining by itself is very unstable process because hardware is pushed to the limits. Something can always go wrong. NiceHash QuickMiner will in most cases take care of all the issues, but sometimes, it cannot do on it's own and needs your command. There are two scenarios that can happen and three possibilities how NiceHash QuickMiner can react.

Scenario | Possible action | Config name | Default action
---------|-----------------|-------------|---------------
Excavator shows abnormally high speed | Do nothing `1`<br>Restart Excavator `2`<br>Restart PC `3` | `"whenDeviceSpeedTooHigh"` | `2`
Excavator shows speed zero | Do nothing `1`<br>Restart Excavator `2`<br>Restart PC `3` | `"whenDeviceSpeedZero"` | `1`

When device is malfunction and not mining, Error will be displayed in [Rig Manager](https://www.nicehash.com/my/mining/rigs) as visible on the following picture.

![Device error](https://github.com/nicehash/NiceHashQuickMiner/blob/main/images/error.png?raw=true)

We suggest you to try to set action to number `2` (Restart Excavator). If that does not help and resolve the issue automatically, then set this to number `3`.  The above mentioned config values can be found in nhqm.conf (NiceHash QuickMiner right click notification icon and choose `Settings` -> `Edit config file`).