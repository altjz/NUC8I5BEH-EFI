# NUC8I5BEH EFI for Catalina

## [中文](./README.md)

## Change Log

### 2020-09-14

    1. Fix Bluetooth cannot turn off.

### 2020-08-15

    1. Using Open Core instead of Clover
    2. Using Original Intel Wifi and Bluetooth
    3. Using Nvme 970Evo instead of SATA，🚀🚀🚀

## Hardware Specification

| Hardware       | Model                | Others                               |
| -------------- | -------------------- | ------------------------------------ |
| Board Model    | NUC8I5BEH            |                                      |
| BIOS Version   | 75                   |                                      |
| WIFI           | Intel 9560           |                                      |
| Bluetooth      | Intel 9560           |                                      |
| RAM            | DDR4 2666 16G x2     | NUC only support 2400                |
| HardDisk       | SAMSUMG 970 EVO 500G |                                      |
| Monitor HDMI   | HKC T7000 2K         |                                      |
| Monitor USBC-C | 15.6 portable        | Signal and Power supply using Type-C |

## BIOS Settings

1. Disable Secure Boot  
2. Disable Legacy Boot  
3. Disable LAN / WIFI Boot  

## OpenCore Version

0.5.9

## Support Features

1. Compatible up to 10.15.6
2. Support Internal Intel WIFI and Bluetooth
3. Support Type-C + HDMI daul Monitors (support hot plugin)
4. Support DP HDMI Audio
5. USB normal
6. 3.5 linein Audio
7. CPU Turbo
8. Sleep/Awake

## Known Issues

1. ExpressCard

   Not Working at all, you can use thi command to hide the Icon

```shell
fn=".`date +%s`" && sudo mv /System/Library/CoreServices/Menu\ Extras/ExpressCard.menu /System/Library/CoreServices/Menu\ Extras/ExpressCard.menu$fn && sudo touch /System/Library/CoreServices/Menu\ Extras/ExpressCard.menu
```

2. HandOff Airdrop Not Working at all, Intel Wifi Driver using Ethernet actually.

3. Network Monitoring (iStats Menu) Download Speed awalys be 0, Solution Please reference this issue [网速监控下载速度一直是0](https://github.com/OpenIntelWireless/itlwm/issues/172)

4. Not working on Bluetooth Low Energy 4.0 (Logitech Master 2s)

## Supplyment

- Wifi: Thanks to [itlwm](https://github.com/OpenIntelWireless/itlwm)，Now we can use the internal Wifi, Please Download the GUI WIFI [HeliPort](https://github.com/OpenIntelWireless/HeliPort), And Please remember enable the Wifi/Bluetooth in BIOS
- SerialNumber: Please modify your Serial Number，you could use Clover Configurator to generate a new one.
- NUC8I7BEx: CPU is the only difference, I suppose this should work.

## References

1. [NUC8（豆子峡谷）黑苹果新手指南Q&A](https://www.jianshu.com/p/b298da6afef3)
2. [NUC8BEX 黑苹果维护教程](https://www.jianshu.com/p/2b8516276147)
3. [Open Intel Wifi](https://github.com/OpenIntelWireless/itlwm)
4. [Intel Bluetooth Firmware](https://github.com/OpenIntelWireless/IntelBluetoothFirmware)
5. [csrutil/NUC8I5BEH](https://github.com/csrutil/NUC8I5BEH)
