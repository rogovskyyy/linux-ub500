# Fix UB500 driver problem (Bluetooth 5 devices) on Linux
## Before you start - make sure you're missing UB500 driver.
```
lsusb; dmesg | egrep -i 'blue|firm'
```

If it says something like
```
[    6.019483] Bluetooth: hci0: RTL: loading rtl_bt/rtl8761b_fw.bin
[    6.019814] bluetooth hci0: Direct firmware load for rtl_bt/rtl8761b_fw.bin failed with error -2
[    6.019818] Bluetooth: hci0: RTL: firmware file rtl_bt/rtl8761b_fw.bin not found
```

Simply put 
```
rtl8761b_fw.bin
rtl8761b_config.bin
```
into
```
/lib/firmware/rtl_bt
```
and replug the bluetooth module.

Voilà

## Tested on TP-Link UB500 & Ubuntu 20.04 LTS

## Useful link
https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/commit/?id=7118987b2f7aff733573121607bc9640a4880296
