# project_path
<!-- keep the format ktf-->
## Download the latest image from armbian archive [![alt text][1]](https://rsync.armbian.com/oldarchive/jetson-nano/archive/)
<!-- ktf-->
Latest image on webpage [![alt text][1]]( https://rsync.armbian.com/oldarchive/jetson-nano/archive/Armbian_23.8.1_Jetson-nano_bookworm_current_6.1.50_xfce_desktop.img.xz)
<!-- ktf -->
## unpack the file - format xz
<!-- ktf -->
- unxz --help => Compress or decompress FILEs in the .xz format.
<!-- ktf -->
```bash <!-- markdownlint-disable-line code-block-style -->
# goto to download folder and decompress
unxz -d  Armbian_23.8.1_Jetson-nano_bookworm_current_6.1.50_xfce_desktop.img.xz
```
<!-- ktf -->
## find device from usb stick
<!-- ktf -->
```bash <!-- markdownlint-disable-line code-block-style -->
# the last on - compare the plugged/ unplugged status
lsblk
```
<!-- ktf -->
>[!NOTE]
>In our case was the /dev/sdb1
<!-- ktf -->
## format usb stick - for a clean starting position
<!-- ktf -->
```bash <!-- markdownlint-disable-line code-block-style -->
sudo mkfs.vfat -F 32 -n "NEW_USB" /dev/sdb1
```
<!-- ktf -->
## write to usb stick via bach command dd
<!-- ktf -->
```bash <!-- markdownlint-disable-line code-block-style -->
 sudo dd bs=4M if=/home/trapapa/Downloads/Armbian_23.8.1_Jetson-nano_bookworm_current_6.1.50_xfce_desktop.img of=/dev/sdb status=progress oflag=sync
```
<!-- ktf -->
## Collected problems and challenges
<!-- ktf -->
- No login prompt after apt update - web search [![alt text][1]](https://duckduckgo.com/?q=linux+debian+No+login+prompt+after+apt+update&t=vivaldi&atb=v484-1&ia=web)
<!-- ktf -->
## Chroot os from another usb disk
<!-- ktf-->
- list connected disk - lsblk - list block devices
<!-- ktf -->
<!-- ktf -->
```bash <!-- markdownlint-disable-line code-block-style -->
```
<!-- ktf -->
```bash <!-- markdownlint-disable-line code-block-style -->
# as root
lsblk
#output
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    1  28.6G  0 disk 
└─sda1   8:1    1  28.3G  0 part /
sdb      8:16   0 465.8G  0 disk 
└─sdb1   8:17   0 461.1G  0 part 
zram0  252:0    0   1.9G  0 disk [SWAP]
zram1  252:1    0    50M  0 disk /var/log
```
<!-- ktf -->
- mount disk/partition
<!-- ktf -->
```bash <!-- markdownlint-disable-line code-block-style -->
# as root
mount /dev/sdb1 /mnt/mychroot
# check it is mounted already
ls -la /mnt/mychroot
# output skip
```
<!-- ktf -->
- mount
<!-- ktf -->
```bash <!-- markdownlint-disable-line code-block-style -->
sudo mount -t proc /proc /mnt/mychroot/proc
sudo mount -t sysfs /sys /mnt/mychroot/sys
sudo mount --bind /dev /mnt/mychroot/dev
sudo mount --bind /dev/pts /mnt/mychroot/dev/pts
```
<!-- ktf -->
- next point
<!-- To comply with the format -->
<!-- Link sign - Don't Found a better way :-( - You know a better method? - send me a email -->
>[!NOTE]
>Symbol to mark web external links [![alt text][1]](./README.md)
<!-- spell-checker: disable  -->
<!-- keep the format -->
<!-- make folder and download the link sign vai curl -->
<!-- mkdir -p img && curl --create-dirs --output-dir img -O  "https://raw.githubusercontent.com/MathiasStadler/link_symbol_svg/refs/heads/main/link_symbol.svg"-->
<!-- Link sign - Don't Found a better way :-( - You know a better method? - **send me a email** -->
[1]: ./img/link_symbol.svg
<!-- keep the format -->