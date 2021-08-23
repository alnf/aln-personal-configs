# Software <!-- omit in toc -->

- [VSCode](#vscode)
- [Bash](#bash)
- [Starship](#starship)
- [Miniconda](#miniconda)
- [Z script](#z-script)
- [Jupyter](#jupyter)
- [Google Translate](#google-translate)
- [TeamViewer](#teamviewer)
- [Python](#python)
- [Ubuntu desktop](#ubuntu-desktop)
- [Gmail](#gmail)
- [Gnome-terminal](#gnome-terminal)
- [Mamba](#mamba)
- [Firefox](#firefox)

## [VSCode](https://code.visualstudio.com/)

Extensions:

- markdownlint (David Anson)
- Python (Microsoft)
- Markdown All in One (Yu Zhang). Toggle view with CTRL+SHIFT+V.

## Bash

Get CPU, HDD, memory stats:

```bash
echo "CPU `LC_ALL=C top -bn2 | grep "Cpu(s)" | tail -n1 | sed "s/.*, *\([0-9.]*\)%* id.*/\1/" | awk '{print 100 - $1}'`% RAM `free -m | awk '/Mem:/ { printf("%3.1f%%", $3/$2*100) }'` HDD `df -h / | awk '/\// {print $(NF-1)}'`"
```

Set unlimited history:

```bash
HISTSIZE=-1
HISTFILESIZE=-1
```

And for older bash versions:

```bash
HISTSIZE=
HISTFILESIZE=
```

## [Starship](https://starship.rs)

I don't use conda base environment as my default environment, so I want to see `base` in my prompt.

```bash
cat ~/.config/starship.toml 
[conda]
ignore_base=false
```

To enable **Starship** and control console tab naming add this to `.bashrc` or `.profile` or `.bash_profile` (depends on your system and circumstances):

```bash
eval "$(starship init bash)"
function set_win_title(){
    echo -ne "\033]0;TRMNL --- $USER@$HOSTNAME:$(basename $PWD)\007"
}
starship_precmd_user_func="set_win_title"
```

How to instsall on remote host:

```bash
curl https://sh.rustup.rs -sSf | sh
source $HOME/.cargo/env
cargo install starship
```

To use with screen add the following line to `.screenrc` file:

```bash
shell -$SHELL
```

## [Miniconda](https://docs.conda.io/en/latest/miniconda.html)

To turn off activating base by default:

```bash
conda config --set auto_activate_base false
```

Updating conda:

```bash
conda update -n base -c defaults conda
```

## [Z script](https://github.com/rupa/z)

Basically follow the instructions in the repop. To install man page, do following:

```bash
sudo cp z.1 /usr/local/man/man1/
sudo mandb
```

## Jupyter

Add conda environment as kernel ([source article](https://medium.com/@nrk25693/how-to-add-your-conda-environment-to-your-jupyter-notebook-in-just-4-steps-abeab8b8d084)):

```bash
conda install -c anaconda ipykernel
python -m ipykernel install --user --name=myenv
```

Additional package might be needed in the target env:

```bash
conda install nb_conda
```

## [Google Translate](https://translate.google.com/)

How to use Google Translate API to get translation of any highlighted piece of text ([source article](http://www.webupd8.org/2016/03/translate-any-text-you-select-on-your.html)):

```bash
#!/usr/bin/env bash
text="$(xsel -o)"
translate="$(wget -U "Mozilla/5.0" -qO - "http://translate.googleapis.com/translate_a/single?client=gtx&sl=auto&tl=en&dt=t&q=$(echo $text | sed "s/[\"'<>]//g")" | sed "s/,,,0]],,.*//g" | awk -F'"' '{print $2, $6}')"
echo -e "Original text:" "$text"'\n' > /tmp/gtrans
echo "Translation:" `echo "$translate" | sed -n 1p` >> /tmp/gtrans
zenity --text-info --title="Translation" --filename=/tmp/gtrans
```

## [TeamViewer](https://www.teamviewer.com)

To disable running as a demon in the background

```bash
sudo teamviewer --daemon disable
```

## Python

For Ubuntu 20.04 to get proper alias:

```bash
sudo apt install python-is-python3
```

## Ubuntu desktop

[Shortcuts](https://help.ubuntu.com/stable/ubuntu-help/shell-keyboard-shortcuts.html.en) (I can never remember them).

Some application can't be added as favorites because of wrong `StartupWMClass` line in the `.desktop` launcher. Here is [fix](https://askubuntu.com/questions/975178/duplicate-application-icons-in-ubuntu-dock-upon-launch/975230#975230).

Fixing keyboard leyout switch and other things:

```bash
sudo apt-get install gnome-tweaks
```

Swiching from Wayland to Xorg [manual](https://fostips.com/switch-back-xorg-ubuntu-21-04/).

Extentions:

- [Moving windows](https://extensions.gnome.org/extension/16/) to a specific workspace extention.
- [Unite](https://extensions.gnome.org/extension/1287/unite/) - windows laoyout tweaks, some kind of global menu.

## Gmail

How to [set up link](https://www.getmailflow.com/post/gmail-desktop-app) to call from Chrome with shortcut.

Or you can pin the tab:)

## Gnome-terminal

[Color schemes](https://github.com/Mayccoll/Gogh).

## [Mamba](https://github.com/mamba-org/mamba)

MAMBA IS LIFE!!!

## Firefox

Add-ons:

- Tree Style Tab
