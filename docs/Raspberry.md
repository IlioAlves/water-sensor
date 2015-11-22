# Connect raspberry with ESP8266

![Source: http://www.esp8266.com/wiki/doku.php?id=raspberrypi:getting_started](schemas/5.png)

Connect the raspberry with ESP8266 as the image above.

# Installing the firmware

Download esptool.py:
* [Esptool](https://github.com/themadinventor/esptool)

Download NodeMCU:
* [NodeMCU](https://github.com/nodemcu/nodemcu-firmware/releases)

connect ESP8266 to USBSerial (Connect the GPI0 to the ground):
![Source: http://iot-playground.com/images/articles/016/esp8266-reflash-firmware.png](schemas/1.png)

![Source: https://raw.githubusercontent.com/guyz/pyesp8266/master/esp8266_pinout.png](schemas/2.png)

Then, run:
```
./esptool.py --port=/dev/ttyAMA0 write_flash -fm=dio -fs=32m 0x00000 nodemcu_float_0.9.6-dev_20150704\ 2.bin
```

It will return:
> Connecting...
> 
> Erasing flash...
> 
> Wrote 462848 bytes at 0x00000000 in 45.4 seconds (81.6 kbit/s)...
> 
> 
> Leaving...

Disconnect and connect the USB again

* If the esptool didn't work and return "Failed to connect to ESP8266", try to desconnect and connect the 3.3V from the ESP.

# [OFFTOPIC] WIFI on Raspberry

```
vim /etc/network/interfaces
```

> auto wlan0
> allow-hotplug wlan0
> iface wlan0 inet dhcp
> wpa-ssid "WIFI_NAME"
> wpa-psk "WIFI_PASS"

```
ifdown wlan0
ifup wlan1
```

[http://randomnerdtutorials.com/how-to-make-two-esp8266-talk/](http://randomnerdtutorials.com/how-to-make-two-esp8266-talk/)

# Useful Links

[https://projects.drogon.net/raspberry-pi/wiringpi/pins/](https://projects.drogon.net/raspberry-pi/wiringpi/pins/)