# Software <!-- omit in toc -->

- [VSCode](#vscode)
- [Starship](#starship)
- [Conda](#conda)
- [Z script](#z-script)

## [VSCode](https://code.visualstudio.com/)

Extensions:

* markdownlint (David Anson)
* Python (Microsoft)
* Markdown All in One (Yu Zhang)

## [Starship](https://starship.rs)

I don't use conda base environment as my default environment, so I want to see `base` in my prompt.

```bash
cat ~/.config/starship.toml 
[conda]
ignore_base=false
```

To enable **Starship** and control console tab naming add this to `.bashrc` or `.profile` (depends on your system):

```bash
eval "$(starship init bash)"
function set_win_title(){
    echo -ne "\033]0;TRMNL --- $USER@$HOSTNAME:$(basename $PWD)\007"
}
starship_precmd_user_func="set_win_title"
```

## Conda

TODO

## Z script

TOOD