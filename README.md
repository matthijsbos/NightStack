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

### Layout
![](/doc/img/front-layout.png)

### Specifications
| Name   | Device                       | CPU                 | RAM   | Storage                             | Networking                                               | Description                             |
|--------|------------------------------|---------------------|-------|-------------------------------------|----------------------------------------------------------|-----------------------------------------|
| SRV-01 | Lenovo ThinkPad Twist s230u  | Intel Core i5 3317U | 4 GB  | 256 GB SSD (mSATA)                  | 1x Onboard Gigabit Ethernet, 1x USB 3.0 Gigabit Ethernet | OpenStack Control Node                  |
| SRV-02 | Dell Inspiron E6330          | Intel Core i5 3320M | 8 GB  | 60 GB SSD (SATA), 500 GB HDD (SATA) | 1x Onboard Gigabit Ethernet, 1x USB 3.0 Gigabit Ethernet | OpenStack Worker Node                   |
| SRV-03 | Dell Inspiron E6330          | Intel Core i5 3340M | 8 GB  | 60 GB SSD (SATA), 320 GB HDD (SATA) | 1x Onboard Gigabit Ethernet, 1x USB 3.0 Gigabit Ethernet | OpenStack Worker Node                   |
| SRV-04 | Dell Inspiron E6330          | Intel Core i5 3340M | 8 GB  | 60 GB SSD (SATA), 320 GB HDD (SATA) | 1x Onboard Gigabit Ethernet, 1x USB 3.0 Gigabit Ethernet | OpenStack Worker Node                   |
| SRV-05 | Dell Inspiron E6330          | Intel Core i5 3340M | 8 GB  | 60 GB SSD (SATA), 320 GB HDD (SATA) | 1x Onboard Gigabit Ethernet, 1x USB 3.0 Gigabit Ethernet | OpenStack Worker Node                   |
| SRV-06 | Dell Inspiron E6330          | Intel Core i5 3320M | 8 GB  | 60 GB SSD (SATA), 320 GB HDD (SATA) | 1x Onboard Gigabit Ethernet, 1x USB 3.0 Gigabit Ethernet | OpenStack Worker Node                   |
| RPI-01 | Raspberry Pi 3 Model B       | Broadcom BCM2837    | 1 GB  | 16 GB SD Card                       | 1x Onboard 100 MBit Ethernet                             | Physical control Node                   |
| AP-01  | GL.iNet microuter-N300       | MediaTek MTK7628NN  | 64 MB | 8 MB Flash                          | 1x Onboard 100 MBit Ethernet, IEEE 802.11b/g/n 300Mbps   | Wi-Fi Access Point                      |
| SW-01  | Linksys LGS326               | N.a.                | N.a.  | N.a.                                | 26x Gigabit Ethernet                                     | Network Switch                          |

### Documentation
| Name                           |  Uri                                                                                                                                                                       |
|--------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Dell E6330 electrical diagrams | [compal_la-7741p_r0.1_schematics.pdf](http://www.s-manuals.com/pdf/motherboard/compal/compal_la-7741p_r0.1_schematics.pdf)                                                 |
| Linksys LGS326 manual          | [ManLgs308Lgs318Lgs326Lgs308PLgs318PLgs326P882001844Revb01En](https://usermanual.wiki/Linksys/ManLgs308Lgs318Lgs326Lgs308PLgs318PLgs326P882001844Revb01En.1664450959/view) |



## Front Panel

### Functionality
| Name  | Description        |
|-------|--------------------|
| BTN1  | Soft power on/off  |
| BTN2  | Unused             |
| BTN3  | Unused             |
| LED1  | SRV-01 status      |
| LED2  | SRV-02 status      |
| LED3  | SRV-03 status      |
| LED4  | SRV-04 status      |
| LED5  | SRV-05 status      |
| LED6  | SRV-06 status      |
| LED7  | Temperature        |
| LED8  | SW-01 status       |
| LED9  | AP-01 status       |
| LED10 | RPI-01 status      |

### LED Status Pattern
| Status   | Pattern      |
|----------|--------------|
| Off      | `----------` |
| Starting | `-----+++++` |
| Stopping | `-----+++++` |
| On/Ok    | `--++++++++` |
| Error    | `---++---++` |

### Rapsberry Pi 3 GPIO Header Pin Assignment

![](https://www.raspberrypi.org/documentation/usage/gpio/images/GPIO-Pinout-Diagram-2.png)

```
                                                                 ---- ----
3v3 === cable 1, lead 1 === blue-white ==<< <<===== 3V3 ========| 01 | 02 |
                                                                 ---- ----
BTN1 == cable 1, lead 2 === blue ========<< <<===== GPIO2 ======| 03 | 04 |
                                                                 ---- ----
BTN2 == cable 1, lead 3 === orange-white =<< <<==== GPIO3 ======| 05 | 06 |
                                                                 ---- ----
1WIRE = cable 1, lead 4 === orange =======<< <<==== GPIO4 ======| 07 | 08 |
                                                                 ---- ----
GND === cable 1, lead 5 === green-white ==<< <<==== GPIO5 ======| 09 | 10 |
                                                                 ---- ----
BTN3 == cable 1, lead 6 === green ========<< <<==== GPIO17 =====| 11 | 12 |
                                                                 ---- ----
LED1 == cable 1, lead 7 === brown-white ==<< <<==== GPIO27 =====| 13 | 14 |
                                                                 ---- ----
LED2 == cable 1, lead 8 === brown ========<< <<==== GPIO22 =====| 15 | 16 |
                                                                 ---- ----
                                                                | 17 | 18 |
                                                                 ---- ----
LED3 == cable 2, lead 1 === blue-white ===<< <<==== GPIO10 =====| 19 | 20 |
                                                                 ---- ----
LED4 == cable 2, lead 2 === blue =========<< <<==== GPIO9 ======| 21 | 22 |
                                                                 ---- ----
LED5 == cable 2, lead 3 === orange-white =<< <<==== GPIO11 =====| 23 | 24 |
                                                                 ---- ----
                                                                | 25 | 26 |
                                                                 ---- ----
                                                                | 27 | 28 |
                                                                 ---- ----
LED6 == cable 2, lead 4 === orange =======<< <<==== GPIO5 ======| 29 | 30 |
                                                                 ---- ----
LED7 == cable 2, lead 5 === green-white ==<< <<==== GPIO6 ======| 31 | 32 |
                                                                 ---- ----
LED8 == cable 2, lead 6 === green ========<< <<==== GPIO13 =====| 33 | 34 |
                                                                 ---- ----
LED9 == cable 2, lead 7 === brown-white ==<< <<==== GPIO19 =====| 35 | 36 |
                                                                 ---- ----
LED10 = cable 2, lead 8 === brown ========<< <<==== GPIO26 =====| 37 | 38 |
                                                                 ---- ----
                                                                | 39 | 40 |
                                                                 ---- ----            
```

### Back Cover Connector

- Green = +5v Fans Right
- Green-White = -5v Fans Right
- Orange = +5v Fans Left
- Orange-White = -5v Fans Left
- Brown = VDD DS18B20 Temperature Sensors
- Brown-White = DQ DS18B20 Temperature Sensors
- Blue = GND DS18B20 Temperature Sensors
- Blue-White = Unused

### Temperature Sensors

| Model   | 1Wire Address        | Location                                       |
|---------|----------------------|------------------------------------------------|
| DS18B20 | `28 6016E9371901 43` | intake (h:top d:front w:right)                 |
| DS18B20 | `28 4CA0DF371901 1A` | intake (h:center d:front w:right)              |
| DS18B20 | `28 04D8B3371901 1F` | intake (h:bottom d:front w:center)             |
| DS18B20 | `28 85A016A8013C 17` | exhaust left (h: center: d: back: w: left)     |
| DS18B20 | `28 3A3816A8013C BD` | exhaust right (h: center: d: back: w: right)   |

## Software

### Operating Systems
| Node   | OS           | Version                                                                                                                                           |
|--------|--------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| SRV-01 | Ubuntu       | [Server 20.04.1 LTS AMD64](https://releases.ubuntu.com/20.04.1/ubuntu-20.04.1-live-server-amd64.iso)                                              |
| SRV-02 | Ubuntu       | [Server 20.04.1 LTS AMD64](https://releases.ubuntu.com/20.04.1/ubuntu-20.04.1-live-server-amd64.iso)                                              |
| SRV-03 | Ubuntu       | [Server 20.04.1 LTS AMD64](https://releases.ubuntu.com/20.04.1/ubuntu-20.04.1-live-server-amd64.iso)                                              |
| SRV-04 | Ubuntu       | [Server 20.04.1 LTS AMD64](https://releases.ubuntu.com/20.04.1/ubuntu-20.04.1-live-server-amd64.iso)                                              |
| SRV-05 | Ubuntu       | [Server 20.04.1 LTS AMD64](https://releases.ubuntu.com/20.04.1/ubuntu-20.04.1-live-server-amd64.iso)                                              |
| SRV-06 | Ubuntu       | [Server 20.04.1 LTS AMD64](https://releases.ubuntu.com/20.04.1/ubuntu-20.04.1-live-server-amd64.iso)                                              |
| RPI-01 | Ubuntu       | [Server 20.04.1 LTS Arm64 Raspberry Pi](https://cdimage.ubuntu.com/releases/20.04.1/release/ubuntu-20.04.1-preinstalled-server-arm64+raspi.img.xz)|
| AP-01  | OpenWrt      | [microuter-N300 V3.102](https://docs.gl-inet.com/en/3/release_notes/microuter-n300/)                                                              |

## Network

### Layer 1 - Physical
| SW-01 Interface | Node            | Interface      |
|-----------------|-----------------|----------------|
| 1               | SRV-01          | Onboard LAN    |
| 2               | SRV-02          | Onboard LAN    |
| 3               | SRV-03          | Onboard LAN    |
| 4               | SRV-04          | Onboard LAN    |
| 5               | SRV-05          | Onboard LAN    |
| 6               | SRV-06          | Onboard LAN    |
| 7               | RPI-01          | Onboard LAN    |
| 8               | AP-01           | Onboard LAN    |
| 9               | Front Panel     | STOR           |
| 10              | Front Panel     | MAN            |
| 11              | Front Panel     | PUB2           |
| 12              | Front Panel     | PUB3           |
| 13              | SRV-01          | USB LAN        |
| 14              | SRV-02          | USB LAN        |
| 15              | SRV-03          | USB LAN        |
| 16              | SRV-04          | USB LAN        |
| 17              | SRV-05          | USB LAN        |
| 18              | SRV-06          | USB LAN        |
| 19              | Unused          | Unused         |
| 20              | Unused          | Unused         |
| 21              | Front Panel     | USB-ETH1       |
| 22              | Front Panel     | USB-ETH2       |
| 23              | Front Panel     | PUB1           |
| 24              | Front Panel     | USB-ETH3       |
| 25              | Front Panel     | WAN            |
| 26              | Front Panel     | USB-ETH4       |

![](https://cdn-reichelt.de/bilder/web/xxl_ws/E910/LINKSYS_LGS326_02.png)

### Layer 2 - Virtual LAN (VLAN) Broadcast Domains
> Wake-on-Lan (WoL) does not support VLAN tagging and only works for untagged traffic

| Name               |  VLAN ID | Notes             |
|--------------------|---------:|-------------------|
| Default            |        1 | Disabled          |
| WAN                |       10 |                   |
| Public             |       20 |                   |
| Management         |       30 |                   |
| Storage            |       40 |                   |
| Tenant             |   1000+n | n tenant networks |

### Layer 2 - Media Access
| Node        | Interface   | MAC Address       | WAN (VLAN 10) | Public (VLAN 20) | Management (VLAN 30) | Storage (VLAN 40) | Tenant (VLAN 1000+n) |
|-------------|-------------|-------------------|---------------|------------------|----------------------|-------------------|----------------------|
| SRV-01      | Onboard LAN | B8:88:E3:E0:98:9D |Forbidden      | Tagged           | Untagged             | Forbidden         | Tagged               |
| SRV-01      | USB LAN     | 00:E0:4C:6B:6B:6A | Forbidden     | Forbidden        | Forbidden            | Untagged          | Forbidden            |
| SRV-02      | Onboard LAN | E0:DB:55:E1:CD:98 | Forbidden     | Forbidden        | Untagged             | Forbidden         | Tagged               |
| SRV-02      | USB LAN     | 00:E0:4C:6B:6F:5D | Forbidden     | Forbidden        | Forbidden            | Untagged          | Forbidden            |
| SRV-03      | Onboard LAN | B8:CA:3A:D3:2C:3B | Forbidden     | Forbidden        | Untagged             | Forbidden         | Tagged               |
| SRV-03      | USB LAN     | 00:E0:4C:6B:6E:A1 | Forbidden     | Forbidden        | Forbidden            | Untagged          | Forbidden            |
| SRV-04      | Onboard LAN | F0:1F:AF:22:3A:55 | Forbidden     | Forbidden        | Untagged             | Forbidden         | Tagged               |
| SRV-04      | USB LAN     | 00:E0:4C:6B:6A:4E | Forbidden     | Forbidden        | Forbidden            | Untagged          | Forbidden            |
| SRV-05      | Onboard LAN | F0:1F:AF:2F:2F:9E | Forbidden     | Forbidden        | Untagged             | Forbidden         | Tagged               |
| SRV-05      | USB LAN     | 00:E0:4C:6B:6F:D9 | Forbidden     | Forbidden        | Forbidden            | Untagged          | Forbidden            |
| SRV-06      | Onboard LAN | D4:BE:D9:87:B8:23 | Forbidden     | Forbidden        | Untagged             | Forbidden         | Tagged               |
| SRV-06      | USB LAN     | 00:E0:4C:6B:6E:BA | Forbidden     | Forbidden        | Forbidden            | Untagged          | Forbidden            |
| RPI-01      | Onboard LAN | B8:27:EB:49:B0:4C | Tagged        | Tagged           | Untagged             | Tagged            | Forbidden            |
| SW-01       | Management  | 14:91:82:EC:8E:17 | Forbidden     | Forbidden        | Untagged             | Forbidden         | Forbidden            |
| AP-01       | Onboard LAN | 94:83:C4:04:18:29 | Forbidden     | Forbidden        | Untagged             | Tagged            | Forbidden            |
| Front Panel | STOR        | N.a.              | Forbidden     | Forbidden        | Forbidden            | Untagged          | Forbidden            |
| Front Panel | MAN         | N.a.              | Forbidden     | Forbidden        | Untagged             | Forbidden         | Forbidden            |
| Front Panel | PUB1        | N.a.              | Forbidden     | Untagged         | Forbidden            | Forbidden         | Forbidden            |
| Front Panel | PUB2        | N.a.              | Forbidden     | Untagged         | Forbidden            | Forbidden         | Forbidden            |
| Front Panel | PUB3        | N.a.              | Forbidden     | Untagged         | Forbidden            | Forbidden         | Forbidden            |
| Front Panel | WAN         | N.a.              | Untagged      | Forbidden        | Forbidden            | Forbidden         | Forbidden            |
| Front Panel | USB-ETH1    | 00:0B:05:0E:33:12 | Forbidden     | Forbidden        | Forbidden            | Untagged          | Forbidden            |
| Front Panel | USB-ETH2    | 00:0B:09:15:00:22 | Forbidden     | Forbidden        | Untagged             | Forbidden         | Forbidden            |
| Front Panel | USB-ETH3    | 00:0B:05:0E:33:13 | Forbidden     | Untagged         | Forbidden            | Forbidden         | Forbidden            |
| Front Panel | USB-ETH4    | 00:0B:05:0E:36:09 | Forbidden     | Forbidden        | Forbidden            | Forbidden         | Forbidden            |


### Layer 3 - IPv4 Subnets
| Name       |    CIDR Block |   Subnet Mask |   Host min |     Host Max | Host count |
|------------|--------------:|--------------:|-----------:|-------------:|-----------:|
| Public     |  10.88.0.0/20 | 255.255.240.0 |  10.88.0.1 | 10.88.15.254 |       4094 |
| Management | 10.88.16.0/20 | 255.255.240.0 | 10.88.16.1 | 10.88.31.254 |       4094 |
| Storage    | 10.88.32.0/20 | 255.255.240.0 | 10.88.32.1 | 10.88.47.254 |       4094 |

### Layer 3 - IPv4 Subnet Segments
| Name                      | Address from |   Address to |
|---------------------------|-------------:|-------------:|
| Public - Static lease     |    10.88.0.1 |  10.88.0.254 |
| Public - Floating IPs     |    10.88.1.1 |  10.88.1.254 |
| Public - DHCP dynamic     |   10.88.15.1 | 10.88.15.254 |
| Management - Static lease |   10.88.16.1 | 10.88.16.254 |
| Management - DHCP dynamic |   10.88.31.1 | 10.88.31.254 |
| Storage - Static lease    |   10.88.32.1 | 10.88.32.254 |
| Storage - DHCP dynamic    |   10.88.47.1 | 10.88.47.254 |

### Layer 3 - Node Static IP Lease
| Node   | Interface   | MAC Address       | Public Subnet | Management Subnet | Storage Subnet |
|--------|-------------|-------------------|---------------|-------------------|----------------|
| SRV-01 | Onboard LAN | B8:88:E3:E0:98:9D | 10.88.0.1     | 10.88.16.1        | n.a.           |
| SRV-01 | USB LAN     | 00:E0:4C:6B:6B:6A | n.a.          | n.a.              | 10.88.32.1     |
| SRV-02 | Onboard LAN | E0:DB:55:E1:CD:98 | 10.88.0.2     | 10.88.16.2        | n.a.           |
| SRV-02 | USB LAN     | 00:E0:4C:6B:6F:5D | n.a.          | n.a.              | 10.88.32.2     |
| SRV-03 | Onboard LAN | B8:CA:3A:D3:2C:3B | 10.88.0.3     | 10.88.16.3        | n.a.           |
| SRV-03 | USB LAN     | 00:E0:4C:6B:6E:A1 | n.a.          | n.a.              | 10.88.32.3     |
| SRV-04 | Onboard LAN | F0:1F:AF:22:3A:55 | 10.88.0.4     | 10.88.16.4        | n.a.           |
| SRV-04 | USB LAN     | 00:E0:4C:6B:6A:4E | n.a.          | n.a.              | 10.88.32.4     |
| SRV-05 | Onboard LAN | F0:1F:AF:2F:2F:9E | 10.88.0.5     | 10.88.16.5        | n.a.           |
| SRV-05 | USB LAN     | 00:E0:4C:6B:6F:D9 | n.a.          | n.a.              | 10.88.32.5     |
| SRV-06 | Onboard LAN | D4:BE:D9:87:B8:23 | 10.88.0.6     | 10.88.16.6        | n.a.           |
| SRV-06 | USB LAN     | 00:E0:4C:6B:6E:BA | n.a.          | n.a.              | 10.88.32.6     |
| RPI-01 | Onboard LAN | B8:27:EB:49:B0:4C | 10.88.0.100   | 10.88.16.100      | 10.88.32.100   |
| SW-01  | Management  | 14:91:82:EC:8E:17 | n.a.          | 10.88.16.101      | n.a.           |
| AP-01  | Onboard LAN | 94:83:C4:04:18:29 | n.a.          | 10.88.16.102      | n.a.           |
