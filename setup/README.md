# Setup Desktop (bspwm)

1). run make to install and copy some important files:
```
$ make desktop
```
2). install yay (make sure the Go binary is from pacman and not linuxbrew):
```
$ sudo pacman -Syu --needed base-devel git
$ cd Code && git clone https://aur.archlinux.org/yay.git
$ cd yay && makepkg -si 
```
3). install polybar:
```
$ yay -S polybar
```

# Setup Dev Environment

1). run make to setup the env:
```
$ make dev_env
```

2). install docker:
```
$ wget https://desktop.docker.com/linux/main/amd64/docker-desktop-4.13.0-x86_64.pkg.tar.zst?utm_source=docker&utm_medium=webreferral&utm_campaign=docs-driven-download-linux-amd64
$ sudo pacman -U ./docker-desktop-4.13.0-x86_64.pkg.tar.zst
```
Fix the issue docker-desktop starting:

You need to create 2 files /etc/subuid and /etc/subgid with ranges for user and group id mapping. 
An example:
```
$ echo <USER>:10000:65536 >> /etc/subuid
$ echo <USER>:10000:65536 >> /etc/subgid
```

Start docker-desktop
```
$ systemctl --user start docker-desktop
```

3). install ohmyzsh plugis:
```
$ git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
$ git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

Activate the plugin in ~/.zshrc:
```
plugins=(git docker docker-compose zsh-syntax-highlighting zsh-autosuggestions autojump)
```

4). install tmux plugins:
```
$ tmux source ~/.tmux.conf
$ [ctrl + b] I
```

5). install neovim plugins:
```
$ git clone --depth 1 https://github.com/wbthomason/packer.nvim ~/.local/share/nvim/site/pack/packer/start/packer.nvim
$ nvim --headless -c 'autocmd User PackerComplete quitall' -c 'PackerSync'
$ nvim +PackerSync
$ nvim +PackerCompile
```
