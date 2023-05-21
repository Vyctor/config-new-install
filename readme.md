<p align="center">
	<a href="https://www.linkedin.com/in/vyctorguimaraes/" target="_blank" rel="noopener noreferrer">
    <img alt="Made by" src="https://img.shields.io/badge/made%20by-vyctor%20guimarães-%23FF9000">
  </a>
 <img alt="GitHub" src="https://img.shields.io/github/license/EliasGcf/gobarber?color=%23FF9000">
</p>

# My configuration files

Configuration of path variables and git for a fresh install of OS.

# .zshrc

```
if [[ -r "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh" ]]; then
  source "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh"
fi
[[ ! -f ~/.p10k.zsh ]] || source ~/.p10k.zsh
export AWS_PROFILE=alliedlogistica
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"   
export CARGO_HOME=$HOME/.cargo
export PATH="$PATH:$CARGO_HOME/bin"
export ZSH="$HOME/.oh-my-zsh"
 
#ZSH_THEME="powerlevel10k/powerlevel10k"
ZSH_THEME="dracula-pro"

plugins=(git)
source $ZSH/oh-my-zsh.sh

if [[ ! -f $HOME/.local/share/zinit/zinit.git/zinit.zsh ]]; then
    print -P "%F{33} %F{220}Installing %F{33}ZDHARMA-CONTINUUM%F{220} Initiative Plugin Manager (%F{33}zdharma-continuum/zinit%F{220})…%f"
    command mkdir -p "$HOME/.local/share/zinit" && command chmod g-rwX "$HOME/.local/share/zinit"
    command git clone https://github.com/zdharma-continuum/zinit "$HOME/.local/share/zinit/zinit.git" && \
        print -P "%F{33} %F{34}Installation successful.%f%b" || \
        print -P "%F{160} The clone has failed.%f%b"
fi

source "$HOME/.local/share/zinit/zinit.git/zinit.zsh"
autoload -Uz _zinit
(( ${+_comps} )) && _comps[zinit]=_zinit

zinit ice depth=1; zinit light romkatv/powerlevel10k
zinit light-mode for \
    zdharma-continuum/zinit-annex-as-monitor \
    zdharma-continuum/zinit-annex-bin-gem-node \
    zdharma-continuum/zinit-annex-patch-dl \
    zdharma-continuum/zinit-annex-rust
zinit light zdharma-continuum/fast-syntax-highlighting
zinit light zsh-users/zsh-autosuggestions
zinit light zsh-users/zsh-history-substring-search
zinit light zsh-users/zsh-completions
zinit light buonomo/yarn-completion

pasteinit() {
  OLD_SELF_INSERT=${${(s.:.)widgets[self-insert]}[2,3]}
  zle -N self-insert url-quote-magic  
}

pastefinish() {
  zle -N self-insert $OLD_SELF_INSERT
}
zstyle :bracketed-paste-magic paste-init pasteinit
zstyle :bracketed-paste-magic paste-finish pastefinish

alias cat="bat --style=numbers,changes,grid --paging=always"
alias ls="exa --icons --group-directories-first --git --color=always"
alias top="ytop" 
alias alliedlogistica="export AWS_PROFILE=alliedlogistica"
alias alliedhomologa="export AWS_PROFILE=alliedhomologa"
alias aws-vyctor="export AWS_PROFILE=alliedvyctor"
alias see-git-remote="git remote -v | awk '{print $2}' | uniq"

unsetopt PROMPT_SP
```

# Git config

```
1. Setar o VSCode como editor global
   1. git config --global core.editor code --edit
2. Editar as configurações
   1. git config --global --edit

# Configurações
[user]
	name = Vyctor
	email = dev.vyctor@gmail.com

[core]
	editor = code --wait

[push]
	followTags = true
[alias]
c = !git add --all && git commit -m
s = !git status -s
l = !git log  --pretty=format:'%C(blue)%h%C(red)%d %C(white)%s - %C(cyan)%cn, %C(green)%cr'
amend = !git add --all && git commit --amend --no-edit
count = !git shortlog -s --grep

```

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

Made by Vyctor Guimarães 👋 [See my linkedin](https://www.linkedin.com/in/vyctorguimaraes/)

```

```
