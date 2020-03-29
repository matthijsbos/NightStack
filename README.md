# NightStack

Openstack cluster in a nightstand built out of old laptops.

![](https://media.giphy.com/media/LqmkkOsAVJaXo3Y4OS/giphy.gif)

<!-- ![](https://media.giphy.com/media/idpQH45OkWUMSMWHsc/giphy.gif) -->

## Photos

See onedrive album

https://1drv.ms/a/s!Asv2q6XGbXXnjcFvja_AwGJesQhlCg 

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