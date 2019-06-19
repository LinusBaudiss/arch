# Installation und Einrichtung des LXDE Desktops
---
`pacman -S lxde`  
`mkdir -p ~/.config/openbox`  
`cp /etc/xdg/openbox/menu.xml /etc/xdg/openbox/rc.xml /etc/xdg/openbox/autostart ~/.config/openbox`  
`exec startlxde` in .xinitrc  

            #!/bin/sh
            
            # Kills all your processes when you log out.
            killall --user $USER -TERM

            # Set's the desktop background to solid black. Useful if you have multiple monitors.
            xsetroot -solid black

in `/etc/lxdm/PostLogout`

autologin=linus in `/etc/lxdm/lxdm.conf`