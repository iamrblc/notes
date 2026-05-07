# Machine parameters

- Win 11 Pro / x64
- CPU: AMD Ryzen 7 7900x 8 core 3800 MHz 16 logical processes
- GPU: AMD Radeon (integrated) / Nvidia Geforce RTX 5070
- Baseboard: MSI Micro Star Pro A620M-E (MS-7E28)
- Disk: Capacity 932 GB / Formatted 932 GB / System disk: yes / Page file: Yes / Type: SSD (NVMe)
- Data disk: 4 TB HDD 
- RAM: 64 GB / 5600 MT/s / Form factor: DIMM
# Needs

## Windows

- [x] Praat (Tamsa)
- [x] R (Tamsa)
- [x] R Studio (Tamsa)
- [ ] Altium (Farkas)
- [ ] Integration with SharePoint (Tamsa)
- [ ] VSCode 
## Ubuntu
- [ ] VSCode
- [ ] R
- [ ] Python - numpy, pandas, nibabel, scipy (Farkas, Melina)
- [ ] C (Farkas)
- [ ] QGIS (Farkas)
- [ ] Blender (Farkas)
- [ ] FSL (and related stuff - Melina)
- [ ] Matlab (Melina)

## Dual boot setup

- [ ] Assign 4 TB drive to Data
- [ ] Shrink windows partition
- [ ] install ubuntu with one user
- [ ] add users
	- [ ] Melina
	- [ ] Farkas
	- [ ] Emil

## Check with others

Dear All,

Please revise the planned settings so I can proceed:

The following partitions will be available on the Barks Lab machine:
- 350 GB for Windows 11 
- 250 GB for Ubuntu 24.4
- 380 GB for Data (NTFS)
- Suggestions are welcome. I don't know how much windows "expands" over time with installations, random temp files, etc. and how it can be managed in the future, so I was more generous with that. 

Accesses:
- Windows: one generic user
- Ubuntu: multiple users (for easier workflow with python environment management, git, and other dev works). I would like to add the following users for now: 
	- melina (root)
	- farkas (root)
	- rblc (root)
	- later if needed other users can be added either with root or without.
- Data:
	- permanently mounted as /data under linux
	- accessible from Windows
	- synced with SharePoint (is there a generic barks access? or someone's credetials have to be added?) - this has to be done from Windows
	- (Later further (physical) storage place can be added as data partition.)

Programs:
- Windows:
	- R, R Studio, Praat (already installed)
	- VSCode, python is installed through Windows Subsystem Linux (open power shell and type wsl. It will enter WSL - Ubuntu 24.4. Currently with one user "barks" with pswd "etologia". I expect that people who do dev will hardly ever use windows, this is just a quick gateway if you need to quickly access stuff.)
	- Altium - I got stuck with this one. Farkas, you need to do this because I assume you have the student registration for this.
- Ubuntu (planned):
	- ZSH shell with omyzsh (you can switch to bash if you are barbaric)
	- a global python3 (I'm planning to install 3.11 for compatibility reasons) with probably often used packages (pandas, numpy, plotly, matplotlib, seaborn, scipy, nibabel, ipykernel, etc)
	- uv for package and environment management (I highly recommend to use this and work in project folders in your own environments despite of the global python installation.
	- VSCode 
	- Matlab (we have ELTE licence for this, but you may need to log in individually from your user profiles)
	- LibreOffice
	- Brave Browser
	- Thunderbird
	- Obsidian
	- Teams for Linux (unofficial but works well)
	- Some other programs... but of course if you need something you can use git / apt install / other source code installations. 

Please let me know if you agree with this plan or if you have any questions, suggestions. Then I can move on. 

Thanks,

L.

## GRUB ISSUE

I created an Ubuntu dual boot on a Windows computer the following way:

1. Shrank the windows partition within windows.
2. Using the live usb, I installed Ubuntu to the free space.

Issue: The computer boots to windows directly without giving a grub option to select which OS to load.

What I tried:
1. Setting up boot priority in BIOS (MSI). However, there I found no option for this (only cd, usb, floppy, hard drive - and within hard drive there was no option to select windows / linux)
2. I booted from the live usb, checked sudo fdisk -l. This cleared that ubuntu was installed properly: 
   - **dev/nvme0n1p1** = 200 MB EFI System Partition
- **/dev/nvme0n1p3** = Windows
- **/dev/nvme0n1p5** = **449 GB Linux filesystem**
1. I tried this:
```bash
sudo mount /dev/nvme0n1p5 /mnt
sudo mount /dev/nvme0n1p1 /mnt/boot/efi
sudo grub-install --boot-directory=/mnt/boot --efi-directory=/mnt/boot/efi /dev/nvme0n1
```
This output "installation finished, no error reported"

Then 
```bash
sudo chroot /mnt update-grub
```
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?)

Then i did bindings:
```bash
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt update-grub
```

Still no grub after reboot.

Question: Knowing this situation, what seems to be the issue?Would it be better to start the ubuntu installation afresh and try to fix the grub issue during that process somehow or try fixing the issue with coding workarounds like I tried before?



