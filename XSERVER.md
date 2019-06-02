# Installation des x-Server
* Installation von xorg-server xorg-xinit xorg-xsetroot xorg-xbacklight xf86-video-intel ttf-dejavu
* st
`git clone https://aur.archlinux.org/st.git`
* Kopiere der st_config.h aus git nach ~/st/config.h
`makepkg -s`
`makepkg --install`
* dwm
`git clone https://aur.archlinux.org/dwm.git`
* Kopiere der dwm_config.h aus git nach ~/dwm/config.h
`makepkg -s`
`makepkg --install`
* acpi installieren
* Kopieren der xinitrc aus git
* Kopieren der xorg.conf aus git nach `/etc/X11/xorg.conf.d`
* Kopieren der zprofile aus git
