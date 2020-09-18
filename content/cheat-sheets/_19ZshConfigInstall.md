+++ 
date = "1979-01-01"
title = "zsh"
description = "zsh config"
+++

<h2 id=ZshConfigInstall>ZshConfigInstall
<img src="https://ohmyz.sh/img/OMZLogo_BnW.png" height="100" width="100" align="right">
</h2>

- `install ohmyzsh` 
``` sh
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

- Install [dracula](https://github.com/dracula/gnome-terminal) for gnome

```sh
# If you come from bash you might have to change your $PATH.
# export PATH=$HOME/bin:/usr/local/bin:$PATH

# Path to your oh-my-zsh installation.
export ZSH="/home/jbjouvin/.oh-my-zsh"

ZSH_THEME="robbyrussell"

# GO
export GOPATH=/home/jbjouvin/go
export PATH="$GOPATH/bin:$PATH"
# END GO

#poetry
export PATH="$HOME/.poetry/bin:$PATH"

#ruby
export GEM_HOME=$(ruby -e 'puts Gem.user_dir')
export PATH="$GEM_HOME/bin:$PATH"

plugins=(
 git
)

autoload -U compinit && compinit

# Sourcing
source $ZSH/oh-my-zsh.sh

# Created by `userpath` on 2019-11-14 22:30:08
export PATH="$PATH:/home/jbjouvin/.local/bin"
```