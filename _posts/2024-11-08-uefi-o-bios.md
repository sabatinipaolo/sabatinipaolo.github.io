---
title: "Il mio sistema è avviato in Uefi o BIOS?"
categories:
  - blog
tags:
  - uefi
  - bios
  - linux 
  - windows


permalink: /blog/uefi-o-bios/
---
TLDR: comandi per verificare se il sistema è partito da Uefi o Bios.

### LINUX

```bash 
    [ -d /sys/firmware/efi ] && echo UEFI || echo BIOS
```
anche altri modi :
[https://www.baeldung.com/linux/uefi-check-machine-boot-method](https://www.baeldung.com/linux/uefi-check-machine-boot-method)



### Windows
[https://www.tenforums.com/tutorials/85195-check-if-windows-10-using-uefi-legacy-bios.html](https://www.tenforums.com/tutorials/85195-check-if-windows-10-using-uefi-legacy-bios.html)
