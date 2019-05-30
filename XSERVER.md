# Installation des x-Server
* Installation von xorg-server xorg-xinit xorg-xsetroot xf86-video-intel ttf-dejavu
* Kopieren der xinitrc (auch Kopie aus git moeglich)
`cp /etc/X11/xinit/xinitrc ~/.xinitrc`
* st
`git clone https://aur.archlinux.org/st.git`
`makepkg -s`
`makepkg --install`
* dwm
`git clone https://aur.archlinux.org/dwm.git`
`makepkg -s`
`makepkg --install`
