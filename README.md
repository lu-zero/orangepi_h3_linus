# The OrangePi-Kernel contains Linux kernel sources (3.4.112 and 4.9) adapted for OrangePI H3 boards, gcc toolchain

The script "build_linux_kernel.sh" can be used to build the kernel.

> The kernel 4.9 supports only USB WLAN MMC UART ETHERNET HDMI OTG. The other functions are currently not supported.


## Example1(how to make uImage 3.4.112)：
    #$ cd OrangePI-Kernel
### clean the kernel tree before build
    #$ sudo ./build_linux_kernel.sh clean clean   
### build the uImage for OPI-PLUS(only two uImage,just plus,pi2),plus,plus2,plus2E use same uIamge,others use pi2 uImage                    
    #$ sudo ./build_linux_kernel.sh plus                              
    #$ cd ../OrangePi-BuildLinux  
### build file system
    #$ sudo ./create_image    
### build plus image                                        
    #$ sudo ./image_from_dir ./linux-trusty orangepi ext4 opi-plus    
    #$ sudo dd bs=4M if=orangepi.img of=/dev/sd*                  
### Read and edit "params.sh" to adjust the parameters to your needs
    #$ $EDITOR params.sh
### If you can not insmod modules,delete directory(/lib/modules) ,then copy /home/orangepi/3.4.112 to /lib/modules/,

### reboot



## Example2(how to make uImage 4.9 and uboot)：
    #$ cd OrangePI-Kernel
### Build the u-boot-sunxi-with-spl.bin and boot.scr for OPI boards
    #$ sudo ./build_mainline_uboot.sh [2 | pc | plus | lite | pc-plus | one | plus2e]    
### Clean the uboot tree before build                   
    #$ sudo ./build_linux_kernel_mainline.sh clean                              
### Build the uImage for OPI                   
    #$ sudo ./build_linux_kernel_mainline.sh opi
    #$ cd ../OrangePi-BuildLinux  
### Build file system
    #$ sudo ./create_image    
### Build plus image                                        
    #$ sudo ./image_from_dir_mainline ./linux-trusty orangepi ext4 opi
    #$ sudo dd bs=4M if=orangepi.img of=/dev/sd*                  
### Read and edit "params.sh" to adjust the parameters to your needs

### Reboot


## Example3(configure desktop)
### After BOOTING,to resize linux partition to fill sd card
    #$ fs_resize
    #$ reboot
### To install desktop run, please wait at least one hours
    #$ install_lxde_desktop  
    #$ reboot
### Install software what your needs(just like follows)


#### Install commom software 
    #$ sudo install_common_software
#### Language from english to chinese
    #$ sudo install_hanhua
#### install mali，use glmark2-es2 test
    #$ sudo install_maliGPU
#### install pepperflash
    #$ sudo install_pepperflash
#### install samba
    #$ sudo install_samba
#### install x2go
    #$ sudo install_x2goserver
#### install vnc
    #$ sudo install_vnc
#### install bypy(you can upload to baiduyun)
    #$ sudo install_bypy
#### install btsync
    #$ sudo install_btsync
#### install ibus chinese input method
    #$ sudo install_ibus_shuru
#### install the camera driver, can be used to provide the official website of the camera
    #$ sudo install_camera_ko



