# NightStack

OpenStack cluster in a nightstand built out of used laptops, used for experimentation.

![](/doc/img/banner.gif)

## Objectives
- Silent
- Limited power comsumption and heat production
- Discrete appearance
- Sufficiently capable performance
- Portable enough to be carried by single person
- No high-availability requirements on hardware

## Photos
See OneDrive album https://1drv.ms/a/s!Asv2q6XGbXXnjcFvja_AwGJesQhlCg 

## Hardware

### Specifications
| Name   | Device                       | CPU                       | RAM  | Storage                             | Networking                                               | Description                             |
|--------|------------------------------|---------------------------|------|-------------------------------------|----------------------------------------------------------|-----------------------------------------|
| SRV-01 | Lenovo ThinkPad Twist s230u  | Intel Core i5 3317U (x64) | 4 GB | 256 GB SSD (mSATA)                  | 1x Onboard Gigabit Ethernet, 1x USB 3.0 Gigabit Ethernet | OpenStack Control Node                  |
| SRV-02 | Dell Inspiron E6330          | Intel Core i5 3320M (x64) | 8 GB | 60 GB SSD (SATA)  500 GB HDD (SATA) | 1x Onboard Gigabit Ethernet, 1x USB 3.0 Gigabit Ethernet | OpenStack Worker Node                   |
| SRV-03 | Dell Inspiron E6330          | Intel Core i5 3340M (x64) | 8 GB | 60 GB SSD (SATA)  320 GB HDD (SATA) | 1x Onboard Gigabit Ethernet, 1x USB 3.0 Gigabit Ethernet | OpenStack Worker Node                   |
| SRV-04 | Dell Inspiron E6330          | Intel Core i5 3340M (x64) | 8 GB | 60 GB SSD (SATA)  320 GB HDD (SATA) | 1x Onboard Gigabit Ethernet, 1x USB 3.0 Gigabit Ethernet | OpenStack Worker Node                   |
| SRV-05 | Dell Inspiron E6330          | Intel Core i5 3340M (x64) | 8 GB | 60 GB SSD (SATA)  320 GB HDD (SATA) | 1x Onboard Gigabit Ethernet, 1x USB 3.0 Gigabit Ethernet | OpenStack Worker Node                   |
| SRV-06 | Dell Inspiron E6330          | Intel Core i5 3320M (x64) | 8 GB | 60 GB SSD (SATA)  320 GB HDD (SATA) | 1x Onboard Gigabit Ethernet, 1x USB 3.0 Gigabit Ethernet | OpenStack Worker Node                   |
| RPI-01 | Raspberry Pi 3 Model B       | Broadcom BCM2837 (ARMv7)  | 1 GB | 16 GB SD Card                       | 1x Onboard 100 MBit Ethernet                             | Physical control Node, WAN Router, DHCP |
| AP-01  | TP-Link TL-WR3020 (Ver 1.9)  | Atheros AR9331            | 32 MB| 4 MB onboard flash                  | 1x Onboard 100 MBit Ethernet, IEEE 802.11b/g/n           | Wi-Fi Access Point                      |
| SW-01  | Linksys LGS326               | N.a.                      | N.a. | N.a.                                | 26x Gigabit Ethernet                                     | Network Switch                          |

### Hardware Documentation
| Name                           |  Uri                                                                                                                                                                       |
|--------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Dell E6330 electrical diagrams | [compal_la-7741p_r0.1_schematics.pdf](http://www.s-manuals.com/pdf/motherboard/compal/compal_la-7741p_r0.1_schematics.pdf)                                                 |
| Linksys LGS326 manual          | [ManLgs308Lgs318Lgs326Lgs308PLgs318PLgs326P882001844Revb01En](https://usermanual.wiki/Linksys/ManLgs308Lgs318Lgs326Lgs308PLgs318PLgs326P882001844Revb01En.1664450959/view) |

### Hardware Layout
![](/doc/img/front-layout.png)

## Network

### Layer 2 - Media Access
| Name   | MAC Address       | Description |
|--------|-------------------|-------------|
| SRV-01 | B8:88:E3:E0:98:9D | Onboard LAN |
| SRV-01 | 00:E0:4C:6B:6B:6A | USB LAN     |
| SRV-02 | E0:DB:55:E1:CD:98 | Onboard LAN |
| SRV-02 | 00:E0:4C:6B:6F:5D | USB LAN     |
| SRV-03 | B8:CA:3A:D3:2C:3B | Onboard LAN |
| SRV-03 | 00:E0:4C:6B:6E:A1 | USB LAN     |
| SRV-04 | F0:1F:AF:22:3A:55 | Onboard LAN |
| SRV-04 | 00:E0:4C:6B:6A:4E | USB LAN     |
| SRV-05 | F0:1F:AF:2F:2F:9E | Onboard LAN |
| SRV-05 | 00:E0:4C:6B:6F:D9 | USB LAN     |
| SRV-06 | D4:BE:D9:87:B8:23 | Onboard LAN |
| SRV-06 | 00:E0:4C:6B:6E:BA | USB LAN     |
| RPI-01 | B8:27:EB:49:B0:4C | Onboard LAN |
| AP-01  | D4:6E:0E:79:E6:BE | Onboard LAN |
| SW-01  | 14:91:82:EC:8E:17 | Management  |

### Layer 2 - Virtual LAN
> Wake-on-Lan (WoL) only works for untagged traffic

| Name       |  VLAN ID | Description       |
|------------|---------:|-------------------|
| Management | Untagged |                   |
| Disabled   |        1 |                   |
| WAN        |       10 |                   |
| Public     |       20 |                   |
| Storage    |       40 |                   |
| Tenant     |   1000+n | n tenant networks |

### Layer 3 - Subnets
| Name       |    CIDR Block |   Subnet Mask |   Host min |     Host Max | Host count |
|------------|--------------:|--------------:|-----------:|-------------:|-----------:|
| Public     |  10.88.0.0/20 | 255.255.240.0 |  10.88.0.1 | 10.88.15.254 |       4094 |
| Management | 10.88.16.0/20 | 255.255.240.0 | 10.88.16.1 | 10.88.31.254 |       4094 |
| Storage    | 10.88.32.0/20 | 255.255.240.0 | 10.88.32.1 | 10.88.47.254 |       4094 |

### Layer 3 - Subnet Segments
| Name                      | Address from |   Address to |
|---------------------------|-------------:|-------------:|
| Public - Static lease     |    10.88.0.1 |  10.88.0.254 |
| Public - floating ips     |    10.88.1.1 |  10.88.1.254 |
| Public - DHCP             |   10.88.15.1 | 10.88.15.254 |
| Management - Static lease |   10.88.16.1 | 10.88.16.254 |
| Management - DHCP         |   10.88.31.1 | 10.88.31.254 |
| Storage - Static lease    |   10.88.32.1 | 10.88.32.254 |
| Storage - DHCP            |   10.88.47.1 | 10.88.47.254 |



## Front Panel

### Rapsberry Pi 3 GPIO Header Pin Assignment

![](https://www.raspberrypi.org/documentation/usage/gpio/images/GPIO-Pinout-Diagram-2.png)

```
                                             ---- ----
                                            | 01 | 02 |
                                             ---- ----
BTN1 ==== cable 1, lead 1 ===== (GPIO 2) -> | 03 | 04 |
                                             ---- ----
BTN2 ==== cable 1, lead 2 ===== (GPIO 3) -> | 05 | 06 | <- GND ========== cable 2, lead 6
                                             ---- ----
BTN3 ==== cable 1, lead 3 ===== (GPIO 4) -> | 07 | 08 |
                                             ---- ----
                                            | 09 | 10 |
                                             ---- ----
LED1 ==== cable 1, lead 4 ==== (GPIO 17) -> | 11 | 12 | <- (GPIO 18) ==== cable 2, lead 1 ==== LED 6 
                                             ---- ----
LED2 ==== cable 1, lead 5 ==== (GPIO 27) -> | 13 | 14 | <- GND ========== cable 2, lead 7
                                             ---- ----
LED3 ==== cable 1, lead 6 ==== (GPIO 22) -> | 15 | 16 | <- (GPIO 23) ==== cable 2, lead 2 ==== LED 7
                                             ---- ----
                                            | 17 | 18 | <- (GPIO 24) ==== cable 2, lead 3 ==== LED 8
                                             ---- ----
LED4 ==== cable 1, lead 7 ==== (GPIO 10) -> | 19 | 20 | <- GND ========== cable 2, lead 8
                                             ---- ----
LED5 ==== cable 1, lead 8 ==== (GPIO 09) -> | 21 | 22 | <- (GPIO 25) ==== cable 2, lead 4 ==== LED 9
                                             ---- ----
                                            | 23 | 24 | <- (GPIO 8) ===== cable 2, lead 5 ==== LED 10
                                             ---- ----
                                            | 25 | 26 |
                                             ---- ----
                                            | 27 | 28 |
                                             ---- ----
                                            | 29 | 30 |
                                             ---- ----
                                            | 31 | 32 |
                                             ---- ----
                                            | 33 | 34 |
                                             ---- ----
                                            | 35 | 36 |
                                             ---- ----
                                            | 37 | 38 |
                                             ---- ----
                                            | 39 | 40 |
                                             ---- ----            
```

## Temperature Sensors

DS18B20

Addresses:

- 286016E937190143 = intake (h:top d:front w:right)
- 284CA0DF3719011A = intake (h:center d:front w:right)
- 2804D8B33719011F = intake (h:bottom d:front w:center)
- 287447D63719014E = exhaust left
- 2872F9E237190157 = exhaust right