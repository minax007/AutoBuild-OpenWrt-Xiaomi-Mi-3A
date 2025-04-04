# AutoBuild-OpenWrt for Xiaomi Mi 3A Router
[![LICENSE](https://img.shields.io/github/license/mashape/apistatus.svg?style=flat&logo=github&label=LICENSE)](https://github.com/esirplayground/AutoBuild-OpenWrt/blob/master/LICENSE)
![GitHub Stars](https://img.shields.io/github/stars/esirplayground/AutoBuild-OpenWrt.svg?style=flat&logo=appveyor&label=Stars&logo=github)
![GitHub Forks](https://img.shields.io/github/forks/esirplayground/AutoBuild-OpenWrt.svg?style=flat&logo=appveyor&label=Forks&logo=github)

![grafik](https://github.com/user-attachments/assets/bdec7b64-908a-44e8-b062-f5635b2d004a)

When the build is complete, click the `Artifacts` button in the upper right corner of the Actions page to download the binaries.

# Flash instruction using sysupgrade image:
1. Acquire SSH access on MiWiFi 3A Router with stock firmware version 2.18.40 by https://github.com/acecilia/OpenWRTInvasion 

2. Set NVRAM values: 
   nvram set uart_en=1
   nvram set bootdelay=5
   nvram set flag_try_sys1_failed=1
   nvram commit

3. Erase operating system partitions: 
   mtd erase OS1
   mtd erase OS2

4. Upload file "openwrt-ramips-mt76x8-xiaomi_miwifi-3a-squashfs-sysupgrade.bin" via FTP into the /tmp directory of the router (IP-adress: 192.168.31.1 | Port:21)

5. Flash OpenWrt to the router: 
   mtd -r write /tmp/openwrt-ramips-mt76x8-xiaomi_miwifi-3a-squashfs-sysupgrade.bin OS1

The router will reboot after the flashing.
Done!
