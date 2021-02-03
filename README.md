# bspwm-arch
## Step 1: active wifi from Network Manager
```
$ nmtui
$ sudo pacman -Syy
```

```
$ sudo pacman -S xf86-video-intel xf86-video-amdgpu xorg bspwm sxhkd rofi nitrogen picom maim kitty qutebrowser chromium lxappearance arc-gtk-theme papirus-icon-theme vlc pcmanfm file-roller pavucontrol bash-completion lightdm lightdm-gtk-greeter pacman-contrib neofetch code galculator evince

```
 
```
$ mkdir .config/bspwm .config/sxhkd .config/polybar
$ cp /usr/share/doc/bspwm/examples/bspwmrc .config/bspwm/
$ cp /usr/share/doc/bspwm/examples/sxhkdrc .config/sxhkd/

$ chmod +x .config/bspwm/bspwmrc
$ chmod +x .config/sxhkd/sxhkdrc

$ nvim .config/sxhkd/sxhkdrc
$ nvim .config/bspwm/bspwmrc

```
```
$ nvim .xinitrc

sxhkd &
exec bspwm
```
```
$ sudo systemctl enable lightdm
```
## Post Installation
#### Install Yay

```
$ cd /opt
$ sudo git clone https://aur.archlinux.org/yay.git
$ sudo chown -R henry:users ./yay
$ cd yay
$ makepkg -si
```

```
$ yay -S polybar pamac-aur siji-git zoom betterlockscreen gotop
```

```
$ nvim .config/polybar/config
$ chmod +x .config/polybar/launch.sh
```
## Set up Betterlockscreen
```
$ sudo pacman -S xorg-xdpyinfo xorg-xrandr bc feh
$ betterlockscreen -u Pictures/arch.png -b 1.0
```
## Set up Pamac Manager
```
$ su
$ cd /etc/polkit-1/rules.d
$ nvim 99-pamac.rules

polkit.addRule(function(action, subject) {
	if (action.id.indexOf("org.freedesktop.pamac-manager.")) {
		return polkit.Result.YES;
	}
});
```
## Remove orphans
```
$ sudo pacman -Qtdq
$ sudo pacman -Rns $(pacman -Qtdq)
```
## Update core editor of git
```
$ git config --global core.editor 'nvim'
```
## Configure Lightdm
```
$ sudo pacman -S lightdm-gtk-greeter-settings

Note: Put PNG or JPG images in /usr/share/pixmaps
```

## Fonts
```
$ sudo pacman -S ttf-font-awesome ttf-cascadia-code ttf-fira-code ttf-droid ttf-joypixels 
```
