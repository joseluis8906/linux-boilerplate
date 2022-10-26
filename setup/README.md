# Setup Desktop (bspwm)

1). run make to install and copy some important files:
```
$ make desktop
```

2). set up polybar:
```
$ git clone --depth=1 https://github.com/adi1090x/polybar-themes.git
$ cd polybar-themes
$ chmod +x setup.sh
```
run and select a theme:
```
$ ./setup.sh

[*] Installing Polybar Themes...

[*] Choose Style -
[1] Simple
[2] Bitmap

[?] Select Option : 1

[*] Installing fonts...
[*] Creating a backup of your polybar configs...
[*] Successfully Installed.
```
to launch the bar with the selected theme:

```
$ bash ~/.config/polybar/launch.sh

Usage : launch.sh --theme

Available Themes :
--blocks    --colorblocks    --cuts      --docky
--forest    --grayblocks     --hack      --material
--panels    --pwidgets       --shades    --shapes
```
now, select your theme and launch the bar:

```
$ bash ~/.config/polybar/launch.sh --hack
```

you can add the same command to your WM autostart file to launch the bar on login.
for example, to launch the bar at startup on openbox, add following lines in 
`~/.xinitrc`

```
## Launch Polybar
bash ~/.config/polybar/launch.sh --hack
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
