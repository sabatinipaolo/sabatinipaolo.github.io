---
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

[Install Windows 10 with larger EFI partition](https://superuser.com/questions/1176310/install-windows-10-with-larger-efi-partition)

[UEFI/GPT-based hard drive partitions](https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions?view=windows-11#recovery-tools-partition)

[https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions?view=windows-11#recovery-tools-partition](https://en.wikipedia.org/wiki/Microsoft_Reserved_Partition#cite_note-GPTFAQ-1)



sudo efibootmgr --create --disk=/dev/sda --part=1 --label="fedora" --loader='EFI\fedora\shimx64.efi'

https://askubuntu.com/questions/342365/what-is-the-difference-between-grubx64-and-shimx64



