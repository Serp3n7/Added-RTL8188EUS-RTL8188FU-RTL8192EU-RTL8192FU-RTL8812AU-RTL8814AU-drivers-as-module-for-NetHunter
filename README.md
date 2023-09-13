
1.  unzip Added-RTL8188EUS-RTL8188FU-RTL8192EU-RTL8192FU-RTL8812AU-RTL8814AU-drivers-as-module-for-NetHunter.zip
2.  copy RTL8188EUS, RTL8188FU, RTL8192EU, RTL8192FU, RTL8812AU, RTL8814AU => Sources Kernel => drivers
3.  cd Sources Kernel => drivers
4.  nano Kconfig
    add
	- source "drivers/bus/Kconfig"
	- source "drivers/rtl8188eus/Kconfig"
    - source "drivers/rtl8188fu/Kconfig"
    - source "drivers/rtl8192eu/Kconfig"
    - source "drivers/rtl8192fu/Kconfig"
    - source "drivers/rtl8812au/Kconfig"
    - source "drivers/rtl8814au/Kconfig"
5.  nano Makefile
    add
    - obj-y					+= bus/
    - obj-y					+= rtl8188eus/
    - obj-y					+= rtl8188fu/
    - obj-y					+= rtl8192eu/
    - obj-y					+= rtl8192fu
    - obj-y					+= rtl8812au/
    - obj-y					+= rtl8814au/
6.  cd Sources Kernel
7.  export ARCH=arm64
8.  export CROSS_COMPILE=aarch64-linux-gnu-
9.  export CROSS_COMPILE_ARM32=arm-linux-gnueabi- 
10. mkdir ../out
11. make O=../out _defconfig
12. make O=../out menuconfig
13. Device drive => 
    - [M] Realtek 8188E USB WiFi
    - [M] Realtek 8188F USB WiFi
    - [M] Realtek 8192E USB WiFi
    - [M] Realtek 8192F/8725AU USB WiFi
    - [M] Realtek 8812A USB WiFi
    - [M] Realtek 8814A USB WiFi
	<save>  
	<exit>
14. make O=../out -j$(nproc)
