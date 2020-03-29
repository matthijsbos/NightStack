# NightStack

OpenStack cluster in a nightstand built out of old laptops.

<!-- ![](https://media.giphy.com/media/LqmkkOsAVJaXo3Y4OS/giphy.gif) -->

![](https://media.giphy.com/media/idpQH45OkWUMSMWHsc/giphy.gif)

## Hardware Specifications
| Name   | Device                           | CPU                          | RAM  | Storage                                 | Networking                                            | Description                                 |
|--------|----------------------------------|------------------------------|------|-----------------------------------------|-------------------------------------------------------|---------------------------------------------|
| SRV-01 | Lenovo<br/>ThinkPad Twist s230u  | Intel<br/>Core i5 3317U      | 4 GB | 256 GB SSD (mSATA)                      | Onboard Gigabit Ethernet<br/>USB 3.0 Gigabit Ethernet | OpenStack Control Node                      |
| SRV-02 | Dell<br/>Inspiron E6330          | Intel<br/>Core i5 3320M      | 8 GB | 60 GB SSD (SATA) <br/>500 GB HDD (SATA) | Onboard Gigabit Ethernet<br/>USB 3.0 Gigabit Ethernet | OpenStack Worker Node                       |
| SRV-03 | Dell<br/>Inspiron E6330          | Intel<br/>Core i5 3340M      | 8 GB | 60 GB SSD (SATA) <br/>320 GB HDD (SATA) | Onboard Gigabit Ethernet<br/>USB 3.0 Gigabit Ethernet | OpenStack Worker Node                       |
| SRV-04 | Dell<br/>Inspiron E6330          | Intel<br/>Core i5 3340M      | 8 GB | 60 GB SSD (SATA) <br/>320 GB HDD (SATA) | Onboard Gigabit Ethernet<br/>USB 3.0 Gigabit Ethernet | OpenStack Worker Node                       |
| SRV-05 | Dell<br/>Inspiron E6330          | Intel<br/>Core i5 3340M      | 8 GB | 60 GB SSD (SATA) <br/>320 GB HDD (SATA) | Onboard Gigabit Ethernet<br/>USB 3.0 Gigabit Ethernet | OpenStack Worker Node                       |
| SRV-06 | Dell<br/>Inspiron E6330          | Intel<br/>Core i5 3320M      | 8 GB | 60 GB SSD (SATA) <br/>320 GB HDD (SATA) | Onboard Gigabit Ethernet<br/>USB 3.0 Gigabit Ethernet | OpenStack Worker Node                       |
| RPI-01 | Raspberry Pi 3<br/>Model B       | Broadcom<br/>BCM2837 (ARMv7) | 1 GB | 16 GB SD Card                           | Onboard 100 MBit Ethernet                             | Physical control Node,<br/>WAN Router, DHCP |
| AP-01  | TP-Link<br/> TL-WR3020 (Ver 1.9) | Atheros AR9331               | 32 MB| 4 MB onboard flash                      | Onboard 100 MBit Ethernet<br>IEEE 802.11b/g/n         | Wi-Fi Access Point                          |
| SW-01  | Linksys<br/>LGS326               | N.a.                         | N.a. | N.a.                                    | 26x Gigabit Ethernet                                  | Network Switch                              |

## Photos

See onedrive album

https://1drv.ms/a/s!Asv2q6XGBXXnjcFvja_AwGJesQhlCg 

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