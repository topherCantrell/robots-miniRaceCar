# robots-miniRaceCar
Based on the Adafruit MyMiniRaceCar

[https://learn.adafruit.com/my-mini-race-car/how-your-robot-works-the-basics?view=all](https://learn.adafruit.com/my-mini-race-car/how-your-robot-works-the-basics?view=all)

# Installing microPython on the Huzzah32

The came with a Bluefruit M0 microcontroller board. I replaced that with the ESP32 Huzzah board.

I installed micropython:

[https://learn.adafruit.com/micropython-basics-how-to-load-micropython-on-a-board/esp8266](https://learn.adafruit.com/micropython-basics-how-to-load-micropython-on-a-board/esp8266)

[http://docs.micropython.org/en/latest/esp8266/esp8266/tutorial/intro.html#deploying-the-firmware](http://docs.micropython.org/en/latest/esp8266/esp8266/tutorial/intro.html#deploying-the-firmware)

```
C:\Python27\Scripts>esptool --port COM7 erase_flash

esptool.py --chip esp32 --port /dev/ttyUSB1 write_flash -z 0x1000 c:\users\tophe\Desktop\esp32-20170902-v1.9.1-477-g75ead22c.bin
```

# The Motor FeatherWing

Product details:
https://learn.adafruit.com/adafruit-stepper-dc-motor-featherwing

Micropython tutorial:
https://learn.adafruit.com/micropython-hardware-pca9685-dc-motor-and-stepper-driver?view=all

Note this is the same chip and communication with the arduino board
