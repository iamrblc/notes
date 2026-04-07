# MINT V1
1. Start
2. F8 -  select usb stick
3. hit tab with Start linux mint ( > /casper/vmlinuz boot=casper initrd=/vasper/initrd.lz uuid=<some number here> username = mint hostname = mint quiet splash --)
4. delete quiet splash and type nomodeset nouveau.modeset=0 modprobe.blacklist=nouveau 3
5. lots of text will scroll and you'll end up with mint login (username should be mint. if it asks for pswd, just hit enter)
6. mint@mint: ~$ sudo -i (this will grant root access)
7. ip a will check the ip devices (probably all will be down)
8. 
```bash
nmcli device set enp5s0 managed yes
nmcli device connect enp5s0
(Then check with ip a)
```
9. lsblk (this will list all the drives)
10. parted /dev/sda --script mklabel gpt (creates clear partition on sda. it's instant. no output will be seen)
11. Create efi partition
    parted /dev/sda --script mkpart ESP fat32 1MiB 513MiB
	parted /dev/sda --script set 1 esp on
12. Create root partition
    parted /dev/sda --script mkpart primary ext4 513MiB 100%
(result should be 512M sda1 and 118GB sda2)
13. Format partitions
    mkfs.fat -F32 /dev/sda1
    mkfs.ext4 /dev/sda2


passwd is just rblc for now




15. Change linux... line to ...quiet rhgb nomodeset 3, then hit F10 to reboot
16. it will show an emergency mode screen. press enter to continue
17. after sh-5.2# type mount -o remount,rw /
18. after this, type journalctl -p 3 -xb (if it says no entries, go on)
19. systemctl default
20. emergency screen again

# V2
1. Start
2. F8 -  select usb stick
3. hit "e" with Try fedora
4. delete rghb and quiet and simply finish the line with inst.text nomodeset

# V3
1. Start
2. F8 -  select usb stick
3. hit "e" with Try fedora
4. delete rghb and quiet, paste quiet rhgb nomodeset nouveau.modeset=0 modprobe.blacklist=nouveau,nvidia,nvidia_drm,nvidia_modeset nvidia.blacklist=yes 3 after root=blabla.image
5. nomodeset video=vesa:off vga=normal nouveau.modeset=0 modprobe.blacklist=nouveau,nvidia,nvidia_drm,nvidia_modeset nvidia.blacklist=yes 3

6. 



GRUB Issue

ls (hd0,gpt2)/boot
output contains vmlinuz, initrd.img

ls (hd0,gpt1)/
output: efi/

ls (hd0,gpt2)/
output: lost+found/ boot/ var/ bin dev/ etc/ home/ lib proc/ root/ run/ sbin sys/ tmp/ usr/ lib64 mnt/ srv/ opt/ media/

When i do ls without the /

ls(hd0, gpt1)
output: partition hd0,gpt1: Filesystem type fat, UUID E41D-074E - Partition start at 1024KiB - Total size 524288KiB

ls(hd0, gpt2)
	output: partition hd0,gpt2: Filesystem type ext* - Last modification time (date is here), UUID 43d461b7-c28d-4872-bba0-89bf22890ce4 - Partition start at 525312KiB - Total size 124509184KiB

set root=(hd0,gpt2)
set prefix=(hd0,gpt2)/boot/grub
insmod normal
normal

nomodeset nouveau.modeset=0 modprobe.blacklist=nouveau systemd.unit=multi-user.target

fedora 43 / linux kernel 6.17
ubuntu 25.10 / linux kernel 6.17

for mokutil reboot stuff the password is 12345678




## System summary

**Hardware**

- Motherboard: ASUS TUF B550M-PLUS WIFI II (UEFI)
    
- CPU: AMD Ryzen (no integrated GPU)
    
- GPU: NVIDIA GeForce RTX 5060 Ti (PCI ID **10de:2d04**)
    
- Storage: NVMe/SATA SSD, UEFI boot
    
- Display: HDMI via NVIDIA GPU (only display device)
    

**OS / Kernel**

- Linux Mint (Ubuntu 24.04 base)
    
- Kernel: **6.14.0-29-generic**
    
- Boot mode: UEFI, Secure Boot disabled for testing
    

**NVIDIA driver**

- Installed: **nvidia-driver-580 (580.95.05)**
    
- DKMS modules built successfully for running kernel
    
- Modules present on disk and loadable (`nvidia.ko`, `nvidia_drm.ko`, etc.)
    
- Kernel module loads without Secure Boot restriction
    

---

## Observed behavior

- NVIDIA kernel module loads and binds to the GPU (`Kernel driver in use: nvidia`)
    
- GPU enumerates correctly on PCI bus
    
- `nvidia-smi` reports **“No devices were found”**
    
- GPU fails to initialize at runtime
    
- Graphical session black-screens when NVIDIA takes over
    
- System works in framebuffer / fallback graphics only
    

---

## Diagnostic steps already taken (to rule out local misconfiguration)

- Verified PCI detection (`lspci -nnk`)
    
- Verified kernel module presence and DKMS build
    
- Verified module loading (`modprobe nvidia`)
    
- Tested with and without Secure Boot
    
- Tested with forced text mode, DRM modeset, and without display manager
    
- Tested multiple boot parameters (`nomodeset`, `nvidia-drm.modeset=1`)
    
- Verified NVIDIA kernel driver version (`/proc/driver/nvidia/version`)
    
- Confirmed no Secure Boot or module-signing blockage
    

---

## One-line diagnosis

**The RTX 5060 Ti (10de:2d04) is not fully supported by the currently available Linux NVIDIA 580.95.05 driver stack; the driver loads but fails to initialize the GPU, resulting in no CUDA device and a black screen when the graphical stack starts.**

---

