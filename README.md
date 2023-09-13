```sh
1.  git clone https://github.com/p3h3n9-pr0j3ct/Added-RTL8188EUS-RTL8188FU-RTL8192EU-RTL8192FU-RTL8812AU-RTL8814AU-drivers-as-module-for-NetHunter.git
2.  cd Added-RTL8188EUS-RTL8188FU-RTL8192EU-RTL8192FU-RTL8812AU-RTL8814AU-drivers-as-module-for-NetHunter.zip
3.  copy RTL8188EUS, RTL8188FU, RTL8192EU, RTL8192FU, RTL8812AU, RTL8814AU => Sources Kernel => drivers
4.  cd Sources Kernel => drivers
5.  nano Kconfig
6.  add
    - source "drivers/bus/Kconfig"
    - source "drivers/rtl8188eus/Kconfig"
    - source "drivers/rtl8188fu/Kconfig"
    - source "drivers/rtl8192eu/Kconfig"
    - source "drivers/rtl8192fu/Kconfig"
    - source "drivers/rtl8812au/Kconfig"
    - source "drivers/rtl8814au/Kconfig"
7.  nano Makefile
8.  add
    - obj-y					+= bus/
    - obj-y					+= rtl8188eus/
    - obj-y					+= rtl8188fu/
    - obj-y					+= rtl8192eu/
    - obj-y					+= rtl8192fu
    - obj-y					+= rtl8812au/
    - obj-y					+= rtl8814au/
9.  cd Sources Kernel
10.  export ARCH=arm64
11.  export CROSS_COMPILE=aarch64-linux-gnu-
12.  export CROSS_COMPILE_ARM32=arm-linux-gnueabi- 
13. mkdir ../out
14. make O=../out "name"_defconfig
15. make O=../out menuconfig
16. Device drive => 
    - [M] Realtek 8188E USB WiFi
    - [M] Realtek 8188F USB WiFi
    - [M] Realtek 8192E USB WiFi
    - [M] Realtek 8192F/8725AU USB WiFi
    - [M] Realtek 8812A USB WiFi
    - [M] Realtek 8814A USB WiFi
17. save  
18. exit
19. make O=../out -j$(nproc)
```
