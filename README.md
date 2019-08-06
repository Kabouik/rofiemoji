# rofiemoji-rofiunicode

Inspired by [fdw/rofimoji](https://github.com/fdw/rofimoji) and its script version by [nkoehring/rofiemoji](https://github.com/nkoehring/rofiemoji), **rofiemoji-rofiunicode** is the combination of two rofi scripts to search emojis or unicode characters directly in rofi, instead of a separate rofi instance like the original [rofimoji by fdw](https://github.com/fdw/rofimoji). Unicode and Emojis modis show up as separate tabs when rofi is invoked:

![rofiemoji-rofiunicode1](.//rofiemoji-rofiunicode1.png)

![rofiemoji-rofiunicode2](.//rofiemoji-rofiunicode2.png)

`rofiemoji.sh` and `rofiunicode.sh` will try to download the lists of emoji and unicode characters when used the first time, unless the full repository has already been cloned using:

```bash
cd ~/.config
git clone https://github.com/Kabouik/rofiemoji.git
```

The list of unicode characters was originally created by [/u/fe80c0ffee](https://www.reddit.com/r/unixporn/comments/7zqkov/oc_i_mad_a_rofi_emoji_picker_and_i_feel_bad_about/duqls53?utm_source=share&utm_medium=web2x).

## Prerequisites

 * An emoji capable font, for example [Noto Emoji](https://www.google.com/get/noto/#emoji-zsye) or [Noto Color Emoji](https://www.google.com/get/noto/#emoji-zsye-color).
 * `xsel` to copy the selection to the clipboard. You should find it in your package manager.

## Usage example
Add a custom keybinding in your system for the following command:
```sh
rofi -show windowcd -theme-str '#window{width: 30%;}' # See the rofi documentation for details
```
Navigate through roji tabs using `Ctrl+Tab` (default) and search emojis or unicode characters by keyword. Pressing `Return` will copy the highlighted character to the clipboard.

## Recommended configuration
For rofi to look like the above screenshots, use the supplied `config` file and `sidetab-adapta.rasi` theme (originally taken from the [rofi-themes](https://raw.githubusercontent.com/davatorium/rofi-themes/master/User%20Themes/sidetab-adapta.rasi) collection):

```bash
mv $HOME/.config/rofi/config $HOME/.config/rofi/config.back
cp $HOME/.config/rofiemoji/config.example $HOME/.config/rofi/config
cp $HOME/.config/rofiemoji/sidetab-adapta.rasi $HOME/.local/share/rofi/themes/
```
The `config` file is customized to my own system and preferences. It is assumed that rofi and rofiemoji folders are located in `~/.config/`. Make sure you reviewed the few uncommented lines to check whether my custom preferences in `config` will work on your system. For instance, this `config` file is adapted to `gnome-terminal`, while default values might work best with other terminals.

## Alternative

An alternative based on [rofimoji by fdw](https://github.com/fdw/rofimoji) instead of rofi-scripts, but still with the addition of unicode characters from [/u/fe80c0ffee](https://www.reddit.com/r/unixporn/comments/7zqkov/oc_i_mad_a_rofi_emoji_picker_and_i_feel_bad_about/duqls53?utm_source=share&utm_medium=web2x) is available here: [Kabouik/rofimoji](https://github.com/Kabouik/rofimoji). It allows multiple selection of emojis or unicode characters, but the window customisation is not as flexible.

![Kabouik/rofimoji](https://reho.st/medium/https://github.com/Kabouik/rofimoji/raw/master/screenshot-fork.png?raw=true)
