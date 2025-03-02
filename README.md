## Installation Instructions
This repository contains Availink AVL62x1 S/S2/S2X demodulator driver and Airoha AV201x tuner driver for Broadcom ARM based set-top box.

Refer to [dvb-frontends-availink](https://github.com/availink/dvb-frontends-availink) and [documentation](https://github.com/availink/documentation) for details related to this code.

### Side Note 

Instructions to build driver are in github and it's easy. (If using Ubuntu 22.04 add ccflags-y += -march=armv7-a to Makefile)
https://github.com/edision-open/dvb-frontends-avl62x1
When avl6261.ko is ready just ftp to /lib/modules/5.15.0/extra/ and reboot.

From here:
https://www.world-of-satellite.com/showthread.php?66349-Display-SNR-when-signal-is-not-locked

### Prerequisites
First install Git and the build dependencies:
- Ubuntu package install
```
sudo apt install git make flex bison libssl-dev gcc gcc-arm-linux-gnueabihf
```
- Fedora package install
```
Comming soon
```


### Getting the Linux kernel
Next get the linux kernel source, which will take some time:
```
wget https://raw.githubusercontent.com/edision-open/edision-kernel/master/edision-kernel-get-latest-source.sh -O - | sh
```

Enter the following commands to prepare kernel modules compilation:
```
cd linux-LATEST_KERNEL_SOURCE_VERSION
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- oldconfig modules_prepare
```


### Build and Install driver module
Clone this repository:
```
git clone https://github.com/edision-open/dvb-frontends-avl62x1.git
```

Build kernel module:
```
cd dvb-frontends-avl62x1
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- KDIR=/PATH/TO/linux-LATEST_KERNEL_SOURCE_VERSION
```

Insert the avl6261.ko kernel module into /lib/modules/LATEST_KERNEL_SOURCE_VERSION/extra/avl6261.ko on your set-top box.


### Blindscan
[Command line blindscan program](https://github.com/edision-open/blindscan) is ready.
