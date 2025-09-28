---
classes: wide
title: "dual boot windows10 ubuntu "
categories:
  - blog
tags:
  - ubuntu
  - windows10
  - winre
  - EFI partition 
  

permalink: /blog/dual-boot-win-ubuntu/
---
TLDR: qualche rogna dell'installare windows e linux in dual boot 

[Linux/Ubuntu not Booting up FixED!!!!](https://www.youtube.com/watch?v=jqOkXvEkdtM)


[How large should you make the UEFI System Partition?](https://www.ctrl.blog/entry/esp-size-guide.html)

[How to change the UEFI System Partition size in Windows Setup ](https://www.ctrl.blog/entry/how-to-esp-windows-setup.html)

Press Shift + F10 to open the Command Prompt
Type diskpart.exe and press Enter to open the disk partitioning tool

Type list disk and press Enter to list out your disks

Type select disk n where n is the number for the disk you want to install to as identified by the above command and press Enter

Type create partition efi size=550 where 550 is the desired size of the ESP in Mebibytes (MiB), and press Enter

Type format quick fs=fat32 label=System and 
press Enter to format the ESP

Type exit and press Enter to exit the disk partitioning tool

Type exit and press Enter again to exit the Command Prompt

Click the Refresh button to detect your partition changes

Select the unallocated space from the disk list and click the New button to automatically recreate the MSR and System partition in the remaining space

[Install Windows 10 with larger EFI partition](https://superuser.com/questions/1176310/install-windows-10-with-larger-efi-partition)

[UEFI/GPT-based hard drive partitions](https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions?view=windows-11#recovery-tools-partition)

[https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions?view=windows-11#recovery-tools-partition](https://en.wikipedia.org/wiki/Microsoft_Reserved_Partition#cite_note-GPTFAQ-1)



sudo efibootmgr --create --disk=/dev/sda --part=1 --label="fedora" --loader='EFI\fedora\shimx64.efi'

https://askubuntu.com/questions/342365/what-is-the-difference-between-grubx64-and-shimx64



