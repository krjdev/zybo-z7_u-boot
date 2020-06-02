# TUTORIAL: Build mainline U-Boot for Digilent ZYBO-Z7 and install on microSD card

**Required hardware**

* Digilent ZYBO Z7 board
* microSD card

**Required software**

* GCC for ARM (aarch32)

## Step 1 - Build U-Boot

*NOTE*  
In this tutorial I usesd the offical GCC compiler from the ARM website.

* Checkout U-Boot sources  
``
$ git clone https://github.com/u-boot/u-boot.git
``  
``
$ cd u-boot
``  
* Build U-Boot  
``
$ export DEVICE_TREE=zynq-zybo-z7
``  
``
$ make mrproper
``  
``
$ make CROSS_COMPILE=/path/to/gcc/bin/arm-none-eabi- -j 4
``

## Step 2 - Install U-Boot on microSD card

There are two options to install U-Boot on the microSD card. The first option is the offical
way. But this option doesn't configure the PL. The second option is to use the FSBL (First
Stage Boot Loader) from Xilinx, which configures the PL.

### Option 1

* Create a FAT32 partition on the microSD card  
``
$ fdisk /dev/sdx
``  
* Create a FAT32 filesystem  
``
$ mkfs.vfat -F 32 /dev/sdx1
``  
* Mount the microSD card  
``
$ mount /dev/sdx /mnt
``  
* Copy the U-Boot SPL (Second Program Loader) to the root directory of the microSD card  
``
$ cp /path/to/U-Boot/spl/boot.bin /mnt
``  
* Copy U-Boot to the microSD  
``
$ cp /path/to/U-Boot/u-boot.img /mnt
``  

### Option 2

Cooming soon.
