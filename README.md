# my own config

Include nvim and tmux

- nvim config path: ~/.config/nvim/init.vim 
- tmux config path: ~/.tmux.conf


# 配置终端和vim为真彩色

## 配置shell为256色


1.检测是否是256色

```bash
awk 'BEGIN{
    s="/\\/\\/\\/\\/\\"; s=s s s s s s s s;
    for (colnum = 0; colnum<77; colnum++) {
        r = 255-(colnum*255/76);
        g = (colnum*510/76);
        b = (colnum*255/76);
        if (g>255) g = 510-g;
        printf "\033[48;2;%d;%d;%dm", r,g,b;
        printf "\033[38;2;%d;%d;%dm", 255-r,255-g,255-b;
        printf "%s\033[0m", substr(s,colnum+1,1);
    }
    printf "\n";
}'
```

2.配置为真彩色

使用`export TERM=xterm-256color`向.bashrc或.zshrc添加256色配置


## vim配置256色

1. 检测是否是256色

```bash
:echo has('termguicolors')
```

2. 配置vim为真彩色

在.vimrc或init.vim中配置vim为正彩色

```bash
if has('termguicolors')
    set termguicolorr
endif
```
