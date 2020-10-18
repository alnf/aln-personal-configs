# Software <!-- omit in toc -->

- [VSCode](#vscode)
- [Starship](#starship)
- [Miniconda](#miniconda)
- [Z script](#z-script)
- [Jupyter](#jupyter)

## [VSCode](https://code.visualstudio.com/)

Extensions:

- markdownlint (David Anson)
- Python (Microsoft)
- Markdown All in One (Yu Zhang)

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

## Z script

TOOD

## Jupyter

Add conda environment as kernel ([source article](https://medium.com/@nrk25693/how-to-add-your-conda-environment-to-your-jupyter-notebook-in-just-4-steps-abeab8b8d084)):

```bash
conda install -c anaconda ipykernel
python -m ipykernel install --user --name=myenv
```
