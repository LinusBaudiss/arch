# How to install a package from aur
---
* Obtain the PKGBUILD. You need to download the tarball that you want. You can find the tarballs for programs at the AUR.
* Make the packages. Next you need to run makepkg in order to generate a package that pacman can install.
`makepkg -cs`
The -c option cleans up the directory after makepkg is done, and -s installs the needed dependencies.

**It is advised that you do NOT run makepkg as root as it can cause permanent damage to your system. If you really need to run it as root though, use the --asroot option.**

* Install the package. makepkg should have create a file in the directory with the filetype .pkg.tar.xz. You should install this package by using the -U option with pacman.
`sudo pacman -U x.pkg.tar.xz`
Make sure you replace x.pkg.tar.xz with the actual package name.

