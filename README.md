# macbook-gpu-fix
Tricks which helps me keep my macbook pro 17 (early 2011) running even if it has broken dedicated gpu.

## notes

1. boot from usb

Following steps
```
csrutil disable
```
and
```
mount -uw /
```
works for me just when I boot from usb.

2. nvram cleanup

Didn't mention any change before I did clean nvram from installed system terminal.

## readings

* http://dosdude1.com/gpudisable/
* https://www.easymacsupport.com/blog/2011-macbook-pro-gpu-failure-repair-disable-amd-and-boot-again
