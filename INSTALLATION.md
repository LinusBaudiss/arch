# Arch Linux Installationssteps
---
## Nützliche Links
[Download](https://www.archlinux.de/download)
[Kurze Installationsanleitung](https://wiki.archlinux.de/title/Arch_Install_Scripts)
[Anleitung für Anfänger](https://wiki.archlinux.de/title/Anleitung_für_Einsteiger)
---
## Vor dem ersten Boot
---)
* Download des Images
* Erstellen eines Bootsticks mit dd
  `dd bs=4M if=/pfad/archlinux-*-x86_64.iso of=/dev/sdX status=progress`
* Überprüfen der Hardwareuhr -> Stellen auf UTC
* Boot von USB im BIOS aktivieren - um ins BIOS zu kommen F1 drücken
  USB HDD als erste Bootoption setzen oder F12 zur Auwahl des Bootmediums nutzen
## Stick-Umgebung
---
* [Partitionierung](https://wiki.archlinux.org/index.php/Partitioning) der Festplatte mit fdisk
* Erstellen der Dateisysteme
* Mounten der Festplatten
* WLAN Verbindung mit wifi-menu herstellen
* Konfigurieren der Mirrorlist
`cp /etc/pacman.d/mirrorlist /etc/pacman.d/mirrorlist.bak`
`grep -E -A 1 ".*Germany.*$" /etc/pacman.d/mirrorlist.bak | sed '/--/d' > /etc/pacman.d/mirrorlist`
* Installieren des Basissystems
`pacstrap /mnt base base-devel intel-ucode bash-completion wpa_supplicant dialog`
* fstab erzeugen und [anpassen](https://wiki.archlinux.de/title/Anleitung_f%C3%BCr_Einsteiger#Das_Basissystem_installieren)
`genfstab -p /mnt > /mnt/etc/fstab`
* Wechsel in die chroot Umgebung
`arch-chroot /mnt`
## Chroot-Umgebung
---
* Setzen des Hostnamens
`echo myhost > /etc/hostname`
* Sprache einstellen
`echo LANG=en_US.UTF-8 > /etc/locale.conf`
* Auskommentieren folgender Zeilen in der /etc/locale.gen
`en_US.UTF-8 UTF-8`
`en_US ISO-8859-1`
* Locale generieren
`locale-gen`
* Einstellen des Tastaturlayouts und der Schriftart
`echo KEYMAP=us > /etc/vconsole.conf`
`echo FONT=lat9w-16 >> /etc/vconsole.conf`
* Setzen der Zeitzone
`ln -sf /usr/share/zoneinfo/Europe/Berlin /etc/localtime`
* Editieren von /etc/hosts -> Localhost Config
`127.0.0.1	localhost.localdomain	localhost`
`::1		localhost.localdomain	localhost`
* Initramfs erzeugen
`mkinitcpio -p linux`
* Root Passwort ändern
* Grub installieren
`pacman -S grub`
`grub-install /dev/sdX`
`grub-mkconfig -o /boot/grub/grub.cfg`
## Arch-Umgebung
* WLAN mit wifi-menu einrichten
* Hinzufügen eines Nutzers
`useradd -m -g users -s /bin/bash linus`
* Installieren von sudo, vim
* Sudo Einrichtung
`EDITOR=nano visudo`
`%wheel ALL=(ALL) ALL`
`gpasswd -a duda wheel`
* Setzen der Uhrzeit
`systemctl enable --now systemd-timesyncd.service`
`date`
`hwclock -w`
* Installieren und einrichten von networkmanger
`sudo systemctl enable NetworkManager.service`
`sudo systemctl start NetworkManager.service`
`sudo nmcli device wifi connect *SSID* password *password*`
* Installieren und starten (s.o.) von acpid.service
