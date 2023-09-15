Reprise de leeloby.
Installer armbian sur OrangePi Zero 3 4Go

pre-req : balena-cli
https://github.com/balena-io/balena-cli/blob/master/INSTALL-LINUX.md
https://github.com/balena-io/balena-cli/releases/tag/v17.1.1
https://github.com/balena-io/balena-cli/releases/download/v17.1.1/balena-cli-v17.1.1-linux-x64-standalone.zip



## Armbian Image**

|:--|:--|:--|
| opizero3 1GB and 2GB memory |ubuntu22.04 xfce |[Armbian_23.08.0-trunk_Orangepizero3_jammy_current_6.1.31_xfce_desktop-1GB-2GB](https://github.com/leeboby/armbian-images/releases/download/opizero3/Armbian_23.08.0-trunk_Orangepizero3_jammy_current_6.1.31_xfce_desktop-1GB-2GB.img.xz)|
| . |ubuntu22.04 server |[Armbian_23.08.0-trunk_Orangepizero3_jammy_current_6.1.31-1GB-2GB](https://github.com/leeboby/armbian-images/releases/download/opizero3/Armbian_23.08.0-trunk_Orangepizero3_jammy_current_6.1.31-1GB-2GB.img.xz)|
| . |debian12 xfce |[Armbian_23.08.0-trunk_Orangepizero3_bookworm_current_6.1.31_xfce_desktop-1GB-2GB](https://github.com/leeboby/armbian-images/releases/download/opizero3/Armbian_23.08.0-trunk_Orangepizero3_bookworm_current_6.1.31_xfce_desktop-1GB-2GB.img.xz)|
| . |debian12 server | [Armbian_23.08.0-trunk_Orangepizero3_bookworm_current_6.1.31-1GB-2GB](https://github.com/leeboby/armbian-images/releases/download/opizero3/Armbian_23.08.0-trunk_Orangepizero3_bookworm_current_6.1.31-1GB-2GB.img.xz) |

Then Download the below 
. (https://github.com/leeboby/opizero3-uboot-kernel/blob/main/u-boot-sunxi-with-spl-opizero3-4gb.bin)4gb memory u-boot bin file
. (https://github.com/leeboby/opizero3-uboot-kernel/blob/main/sun50i-h616-orangepi-zero3-4gb.dtb)4gb memory dtb file

[image](https://github.com/enoola/armbian-images-OPi_Zero_3_4GB/assets/25523012/69473bfc-6588-4566-9f16-4775d4f9d07a)


$ sudo balena local flash /media/psf/Home/Workspace/OrangePiZero3/Armbian/Armbian_23.08.0-trunk_Orangepizero3_bookworm_current_6.1.31-1GB-2GB.img.xz
Enter
Enter
![image](https://github.com/enoola/armbian-images-OPi_Zero_3_4GB/assets/25523012/99faa180-4188-4e21-8fdd-41e25f8ab1e1)
Flashing [========================] 100% eta 0s   
Validating [========================] 100% eta 0s  

$ sudo mount /dev/sdb1 /mnt
$ sudo cp -fv flash /home/user/OrangePiZero3/Armbian/sun50i-h616-orangepi-zero3-4gb.dtb /mnt/boot/dtb/allwinner/sun50i-h616-orangepi-zero3.dtb 
'/home/user/OrangePiZero3/Armbian/sun50i-h616-orangepi-zero3-4gb.dtb' -> '/mnt/boot/dtb/allwinner/sun50i-h616-orangepi-zero3.dtb'
$ openssl sha1 /home/user/OrangePiZero3/Armbian/sun50i-h616-orangepi-zero3-4gb.dtb
SHA1(/home/user/OrangePiZero3/Armbian/sun50i-h616-orangepi-zero3.dtb)= 66e47e382f26f90a034c8a7d330aa25a546102f0
$ openssl sha1 /mnt/boot/dtb/allwinner/sun50i-h616-orangepi-zero3.dtb
SHA1(/mnt/boot/dtb/allwinner/sun50i-h616-orangepi-zero3.dtb)= 66e47e382f26f90a034c8a7d330aa25a546102f0

/!\ Very Important !!
$ sudo umount /dev/sdb1 

$ sudo dd bs=1k seek=8 if=/home/user/OrangePiZero3/Armbian/OrangePiZero3/Armbian/u-boot-sunxi-with-spl-opizero3-4gb.bin of=/dev/sdb1
631+1 records in
631+1 records out
646987 bytes (647 kB, 632 KiB) copied, 0.136524 s, 4.7 MB/s

Done 
just boot your OrangePi Zero 3 4GB

---
![image](https://github.com/enoola/armbian-images-OPi_Zero_3_4GB/assets/25523012/4341deba-2ed7-4f06-b6d1-4fdbb80e7fce)

