
+++
title = "Reinstall Windows Bootloader"
date = 2018-06-23T14:17:18+05:30
tags = ["bootloader","windows"]
+++

* Boot from DVD
* go to repaire option
* It will auto dectec the C drive
Go to command prompt

```
bootrec /fixmbr
```
repair the boot loader

```
bootrec /fixboot
```
write new bootloader to MBR