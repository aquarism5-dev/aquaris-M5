WHAT IS THIS?
=============

Linux Kernel source code for the devices:
* BQ Aquaris M5


BUILD INSTRUCTIONS?
===================

Create a M5-KERNEL dir & go into there:

        $ mkdir M5-KERNEL && cd M5-KERNEL

Specific sources are separated by branches and each version is tagged with it's corresponding number. First, you should
clone the project:

        $ git clone https://github.com/aquarism5-dev/aquaris-M5.git

After it, choose the version you would like to build:

* Aquaris M5

        $ mv aquaris-M5 kernel
        $ cd kernel
        $ git checkout aquaris-M5

Go back to the previous dir:

        $ cd ../

At the level of the "M5-KERNEL" directory:

Download a prebuilt gcc

        $ git clone https://android.googlesource.com/platform/prebuilts/gcc/linux-x86/arm/arm-eabi-4.8

Create KERNEL_OUT dir:

        $ mkdir KERNEL_OUT

Your directory tree should look like this:
* /kernel
* /arm-eabi-4.8
* /KERNEL_OUT

Finally, build the kernel by replacing the {product} space in the following line with the real product name, according to the next table of product names, and executing those commands:

| device                                                                                | product                                                               |
| --------------------------|-------------------------|
| bq aquaris M5                                      | piccolo                                      |


        $ make -C kernel  O=../KERNEL_OUT  ARCH=arm CROSS_COMPILE=../arm-eabi-4.8/bin/arm-eabi- {product}_defconfig
        $ make O=../KERNEL_OUT/ -C kernel ARCH=arm  CROSS_COMPILE=../arm-eabi-4.8/bin/arm-eabi-                       
    
You can specify "-j CORES+THREADS" argument to speed-up your compilation, example for a CPU with 4 cores & 4 threads:

        $ make O=../KERNEL_OUT/ -C kernel ARCH=arm  CROSS_COMPILE=../arm-eabi-4.8/bin/arm-eabi- -j 8

Then, your built zImage will be located in M5-KERNEL/KERNEL_OUT/arch/arm/boot.

