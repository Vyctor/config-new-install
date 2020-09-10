1. Setar o VSCode como editor global 
   1. git config --global core.editor code --edit  
2. Editar as configurações
   1. git config --global --edit  

# Configurações

```.gitconfig
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
