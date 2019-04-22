# livelinux 

turns an existing preinstalled Linux System into a Live Kit. This version is a fork from Tomas-M/linux-live and is specially used to create mediakit x86 version based on a preinstalled Debian Distribution (see http://mediakit.education) 

## Getting Started
1. Store Linux Live kit in a directory which is not going to be included
in your live distro i.e. a/:
>sudo mkdir a/

>cd /a

>git clone https://github.com/codekoch/livelinux

2. Before you start building your Kit, edit the file ./config
>cd livelinux

>sudo nano ./config

-Most importantly change the LIVEKITNAME variable and the LIVEKITDATA path.
-Make sure you have enough RAM on the given LIVEKITDATA path since LiveKit will store lots of data there. If you are low on RAM,
  make sure LIVEKITDATA is a regular on-disk directory.
-Make sure your kernel is in /boot/vmlinuz or change the path
-Your kernel must support squashfs and aufs. Debian Jessie's kernel does.
3. Optional:
-You may also wish to replace boot graphics in ./bootfiles/bootlogo.png
  and reorganize isolinux.cfg to fit your needs (when editing the file,
  keep all paths in /boot/, it will be rellocated during LiveKit creation)
-Linux Live Kit comes with precompiled static binaries in ./initramfs
  directory. Those may be outdated but will work. You may replace them
  by your own statically linked binaries, if you know how to compile them.
-If you plan to boot your Live Kit from CD, you need to recompile
  syslinux.bin else it won't be able to boot your Live Kit from directory
  LIVEKITNAME. There is a script prepared for you which will handle all
  of that. Simply go to directory ./tools/ and run isolinux.bin.update ...
  it will update ./bootfiles/isolinux.bin automatically by downloading
  isolinux sources, patching them using your actual LIVEKITNAME and
  recompiling. This step is not needed if you plan to boot from USB only.
4. When done, run the ./build script to create your Live Kit
>sudo ./build.sh

-The following packages will be installed if they are not available:

-- squashfs-tools

-- genisoimage or mkisofs

-- aufs-dkms

-- zip

5. After the successful build you will find your livelinux system under the path
  given by LIVEKITDATA
 
6. To create a bootable device you can use the script createBootDevice.sh under scripts

## Authors

* **Tomas M.** - *initial work* - [Live Linux Kit](http://www.linux-live.org/)

* **Olaf Koch** - *modifications* - [mediakit](http://mediakit.education)
