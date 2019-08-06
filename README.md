# rofiemoji-rofiunicode

Inspired by [fdw/**rofimoji**](https://github.com/fdw/rofimoji) and forked from its script version [nkoehring/**rofiemoji**](https://github.com/nkoehring/rofiemoji), **rofiemoji-rofiunicode** is a character-picker that combines two scripts to search and copy emojis or unicode characters directly from [davatorium/**rofi**](https://github.com/davatorium/rofi).

It comes with an example configuration file and theme that should make it ready to use without user configuration. When using the recommended procedure, unicode and emoji lists show up as separate tabs when rofi is invoked:

![rofiemoji-rofiunicode1](https://github.com/Kabouik/rofiemoji-rofiunicode/blob/master/rofiemoji-rofiunicode1.png?raw=true)

![rofiemoji-rofiunicode2](https://github.com/Kabouik/rofiemoji-rofiunicode/blob/master/rofiemoji-rofiunicode2.png?raw=true)

The two underlying scripts, `rofiemoji.sh` and `rofiunicode.sh`, will try to download the lists of emoji and unicode characters if they are missing, but this should already been taken care of when cloning this repository as follows:

```bash
cd ~/.config # Using this path is important for next steps
git clone https://github.com/Kabouik/rofiemoji-rofiunicode.git
```

The list of emojis is fetched from www.unicode.org while the unicode list was created by [/u/fe80c0ffee](https://www.reddit.com/r/unixporn/comments/7zqkov/oc_i_mad_a_rofi_emoji_picker_and_i_feel_bad_about/duqls53?utm_source=share&utm_medium=web2x).

## Prerequisites

 * An emoji capable font, for example [Noto Emoji](https://www.google.com/get/noto/#emoji-zsye) or [Noto Color Emoji](https://www.google.com/get/noto/#emoji-zsye-color).
 * `xsel` to copy the selection to the clipboard. You should find it in your package manager.
 * `rofi` from [davatorium/**rofi**](https://github.com/davatorium/rofi) but probably available in your package manager as well.

## Usage example
Add a custom keybinding using your window-manager settings for the following command:

```sh
rofi -show windowcd -theme-str '#window{width: 30%;}' # See the rofi documentation for details
```
Invoke rofi using your keybinding, navigate through tabs using `Ctrl+Tab` (default) and search emojis or unicode characters by keyword. Pressing `Return` will copy the highlighted character to the clipboard and close rofi.

## Recommended configuration
For rofi to look like the above screenshots, use the supplied `config` file and `sidetab-adapta.rasi` theme (originally taken from the [davatorium/**rofi-themes**](https://raw.githubusercontent.com/davatorium/rofi-themes/master/User%20Themes/sidetab-adapta.rasi) collection). This can be done simply by running the following commands:

```bash
mv $HOME/.config/rofi/config $HOME/.config/rofi/config.back
cp $HOME/.config/rofiemoji-rofiunicode/config.example $HOME/.config/rofi/config
mkdir -p $HOME/.local/share/rofi/themes
cp $HOME/.config/rofiemoji-rofiunicode/sidetab-adapta.rasi $HOME/.local/share/rofi/themes/
```
It is assumed, however, that `rofi/` and `rofiemoji-rofiunicode/` directories are both located in `~/.config/`.

The `config` file supplied here is customized to my own preferences and to the characteristics of my system. Make sure you reviewed the few uncommented lines to check whether my changes will work on your system. For instance, this `config` file makes rofi work with gnome-terminal, but default rofi values might work best with other terminals.

## Alternative

[kabouik/**rofimoji**](https://github.com/Kabouik/rofimoji) is an alternative based on the original [fdw/**rofimoji**](https://github.com/fdw/rofimoji) instead of the [nkoehring/**rofiemoji**](https://github.com/nkoehring/rofiemoji) script version, but still with the addition of unicode characters from [/u/fe80c0ffee](https://www.reddit.com/r/unixporn/comments/7zqkov/oc_i_mad_a_rofi_emoji_picker_and_i_feel_bad_about/duqls53?utm_source=share&utm_medium=web2x). It allows multiple selection of emojis or unicode characters, as well as direct input without a clipboard step, but the customization possibilities are more limited and there is no visual unification with your main rofi instance.

![Kabouik/rofimoji](https://github.com/Kabouik/rofimoji/raw/master/screenshot-fork.png?raw=true)
