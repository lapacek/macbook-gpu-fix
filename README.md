# macbook-gpu-fix
Tricks which helps me keep my macbook pro 17 (early 2011) running even if it has broken dedicated gpu.

## step by step guide

You can find original source of this guide [here](#readings). Many thanks to original authors.

```
1. Reset the SMC.

Shutdown the Mac.
Plug it into power.
Hold down for five seconds then release: Left Shift + Ctrl + Option + Power

2. Reset VRAM.

Boot the Mac and hold down the keys: Command + Option + P + R
Continue holding the keys till you hear two chimes. 
Shutdown / power down the Mac.

3. Boot into User Recovery, hold keys during boot until you see the apple logo: Command + R 

In the upper menu select "Utilities" and then "Terminal"
In terminal disable SIP, type and hit return: csrutil disable
Type and hit return: reboot

4. Boot into User Recovery (again), hold keys during boot: Command + R 

In the upper menu select "Utilities" and then "Terminal"
Disable AMD GPU, type and hit return: nvram fa4ce28d-b62f-4c99-9cc3-6815686e30f9:gpu-power-prefs=%01%00%00%00
Enable Verbose Mode, type and hit return: nvram boot-args="-v"
Type and hit return: reboot

5. Boot into Single User, hold keys during boot: Command + S

Mount Root Drive, type and hit return: /sbin/mount -uw /
Make Directory for bad AMD Extension, type and hit return: mkdir -p /System/Library/Extensions-off
Move the AMD Extension, type and hit return: mv /System/Library/Extensions/AMDRadeonX3000.kext /System/Library/Extensions-off/
Update the change, type and hit return: touch /System/Library/Extensions/
Type and hit return: reboot

6. Boot into single user mode (Command + S) and then type: nvram boot-args=“”

Click return and then type: reboot
```

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
works for me just when I boot from usb. Probably I didn't have the recovery partition on my hard drive.

2. nvram cleanup

Didn't mention any change before I did clean nvram from installed system terminal. Then i didn't see my dedicated gpu card enabled anymore.

3. automatic gpu switching

I had to disable automatic gpu swithing in the system settings to solve the freezing after wake up issue.

## readings

* http://dosdude1.com/gpudisable/
* https://www.easymacsupport.com/blog/2011-macbook-pro-gpu-failure-repair-disable-amd-and-boot-again
