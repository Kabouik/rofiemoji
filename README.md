# rofiemoji-rofiunicode

Inspired by [fdw/**rofimoji**](https://github.com/fdw/rofimoji) and forked from its script version [nkoehring/**rofiemoji**](https://github.com/nkoehring/rofiemoji), **rofiemoji-rofiunicode** is a character-picker that allows searching and copying emojis and over 25'000 unicode characters directly from [davatorium/**rofi**](https://github.com/davatorium/rofi).

It comes with an example configuration file and a theme that should make it ready to use, even for those who never used rofi before. When using the recommended procedure, unicode and emoji lists show up as separate tabs in rofi, in addition to rofi's window, drun, run and ssh modis:

![rofiemoji-rofiunicode1](https://github.com/Kabouik/rofiemoji-rofiunicode/blob/master/rofiemoji-rofiunicode1.png?raw=true)

![rofiemoji-rofiunicode2](https://github.com/Kabouik/rofiemoji-rofiunicode/blob/master/rofiemoji-rofiunicode2.png?raw=true)

The two underlying scripts, `rofiemoji.sh` and `rofiunicode.sh`, will try to download the lists of emoji and unicode characters if they are missing, but this should already be taken care of when cloning this repository. The list of emojis is fetched from www.unicode.org while the unicode list was created by [/u/fe80c0ffee](https://www.reddit.com/r/unixporn/comments/7zqkov/oc_i_mad_a_rofi_emoji_picker_and_i_feel_bad_about/duqls53?utm_source=share&utm_medium=web2x).

## Prerequisites

 * `rofi` from [davatorium/**rofi**](https://github.com/davatorium/rofi) or from your package manager.
 * `xsel` to copy the selection to the clipboard. You should find it in your package manager.
 * An emoji capable font, *e.g.*, [Noto Emoji](https://www.google.com/get/noto/#emoji-zsye) or [Noto Color Emoji](https://www.google.com/get/noto/#emoji-zsye-color).

## Installation

1. Clone this repository into `~/.config`:
 ```bash
 cd ~/.config # Using this path is important for next steps
 git clone https://github.com/Kabouik/rofiemoji-rofiunicode.git
 ```

2. (Optional) Apply the [recommended configuration](https://github.com/Kabouik/rofiemoji-rofiunicode#recommended-configuration):

 ```bash
 mv $HOME/.config/rofi/config $HOME/.config/rofi/config.back # Back up previous rofi configuration, if any
 cp $HOME/.config/rofiemoji-rofiunicode/config.example $HOME/.config/rofi/config # Apply the supplied configuration
 mkdir -p $HOME/.local/share/rofi/themes
 cp $HOME/.config/rofiemoji-rofiunicode/sidetab-adapta.rasi $HOME/.local/share/rofi/themes/ # Provide sidetab-adapta.rasi theme
 ```

3. **If step 2 was completed**, add a custom keybinding using your window-manager settings for the following command:

 ```sh
 rofi -show windowcd -theme-str '#window{width: 30%;}' # See the rofi documentation for details
 ```

3. **If step 2 was skipped**, add a custom keybinding using your window-manager settings for a command containing at least the following arguments:

 ```sh
 rofi -show unicode -modi 'unicode:~/.config/rofiemoji-rofiunicode/rofiunicode.sh,emoji:~/.config/rofiemoji-rofiunicode/rofiemoji.sh' -theme-str '#window{width: 30%;}'
 ```

## Usage

1. Invoke rofi using the keybinding you set and navigate through tabs using `Ctrl+Tab` (default).

2. Type a keyword in the emoji or unicode tabs and press `Return` to copy the highlighted character to the clipboard and close rofi.

## Recommended configuration
Users who already configured rofi to their own taste before may prefer to skip installation step 2 to keep their custom changes.

However, for users new to rofi, applying the recommended configuration (installation step 2) should facilitate the setup by configuring everything as in the screenshots. This will move/rename the supplied `config.example` file and the `sidetab-adapta.rasi` theme (taken from the [davatorium/**rofi-themes**](https://raw.githubusercontent.com/davatorium/rofi-themes/master/User%20Themes/sidetab-adapta.rasi) collection) into the adequate folders.

| Make sure you review `config.example` to check if my custom changes will work on your machine. While most of them should be system-agnostic, some settings are tailored to my own use and may not work on all systems. |
| --- |

For instance, the settings in `config.example` make rofi work with gnome-terminal, but default rofi settings might work better when using other terminals. In the latter case, it is best to edit `/.config/rofiemoji-rofiunicode/config.example` before installation step 2 (or `~/.config/rofi/config` after installation step 2) to alter it according to the specific requirements of your system. Alternatively, rofi defaults can be restored by prepending `!` to the following lines to disable them:

Before:
```sh
rofi.terminal: gnome-terminal
rofi.ssh-command: {terminal} -- {ssh-client} {host}
rofi.run-shell-command: {terminal} -- bash -c "{cmd}; bash"
```

After:

```sh
! rofi.terminal: gnome-terminal
! rofi.ssh-command: {terminal} -- {ssh-client} {host}
! rofi.run-shell-command: {terminal} -- bash -c "{cmd}; bash"
```

## Alternative emoji- and unicode-picker

[kabouik/**rofimoji**](https://github.com/Kabouik/rofimoji) is an alternative based on the original [fdw/**rofimoji**](https://github.com/fdw/rofimoji) instead of the [nkoehring/**rofiemoji**](https://github.com/nkoehring/rofiemoji) script version, yet still with the unicode functionality. It allows the multiple selection of emojis or unicode characters, as well as direct input without prior clipboard step, but the customization possibilities are more limited and there is no visual unification with your main rofi instance.

![Kabouik/rofimoji](https://github.com/Kabouik/rofimoji/raw/master/screenshot-fork.png?raw=true)
