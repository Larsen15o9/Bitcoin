**Game Mode is NiceHash QuickMiner's latest feature which makes switching between gaming and mining very easy and quick!**

## 1. What is Game Mode and what does it do?

**Game Mode** performs following activities when activated:
- detects your primary video card,
- stops mining on your primary video card and
- (optional) applies special Game Mode overclock settings for your primary video card.

In reverse, when you deactivate **Game Mode** following is performed:
- primary video card is detected,
- (optional) previous mining overclock settings are applied and
- starts mining on your primary video card.


## 2. Prepare Game Mode

If you do not overclock video card for gaming, you can skip this step and go to the next one.

If you are a gamer who likes to push video card to the limits and does overclocking to get extra FPS, then you would like to apply your favourite overclocks before entering the game. Unfortunately, overclock values for mining are usually complete opposite compared to the ones for gaming therefore, your overclocks need to be changed before entering the game and changed again for mining after exiting the game.

First time using this feature you might want to adjust your `Game Mode Overclock profile`. To do so, right click NiceHash QuickMiner notification icon and from menu select `Game Mode -> Configure`. Following dialog is displayed:

![Game Mode Settings](https://github.com/nicehash/NiceHashQuickMiner/blob/main/images/gm_settings.png?raw=true)

Here, you can tune the most important three parameters for overclocking your gaming GPU. Set them as you are used to and click button `OK`. You are ready to enter **Game Mode** now.

NiceHash QuickMiner automatically detects your primary video card (the one with connected display). **Game Mode** always affects only your primary video card, leaving the rest intact. If, in the future, you change your primary video card to another one, you'd have to reconfigure your **Game Mode** overclocks to fit the new primary video card.


## 3. Entering Game Mode

Right click NiceHash QuickMiner notification icon and from the menu select `Game Mode -> Activate`:

![Game Mode Activate](https://github.com/nicehash/NiceHashQuickMiner/blob/main/images/gm_activate.png?raw=true)

You will be informed whether **Game Mode** activation was successful or if there was an error.


## 4. Leaving Game Mode

When you stop gaming, you can simply return back to full mining by doing the opposite and clicking `Game Mode -> Deactivate`.

