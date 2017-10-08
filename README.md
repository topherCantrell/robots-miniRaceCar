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

# I2C on ESP32

```
from machine import Pin, I2C

esp32i2cPins = {'sda': 23, 'scl': 22}
frequency=100000

sclPin=esp32i2cPins['scl']
sdaPin=esp32i2cPins['sda']
i2c = I2C(scl=Pin(sclPin), sda=Pin(sdaPin), freq = frequency)
        
devices = i2c.scan()
print(devices)  

# Talking to the MCP9808 temperature sensor

address = 24
temp_reg = 5
res_reg = 8

data = i2c.readfrom_mem(address, temp_reg, 2)
print(data)
```

# The Motor FeatherWing

Product details:
https://learn.adafruit.com/adafruit-stepper-dc-motor-featherwing

Micropython tutorial:
https://learn.adafruit.com/micropython-hardware-pca9685-dc-motor-and-stepper-driver?view=all

Note this is the same chip and communication with the arduino board

```
from machine import Pin, I2C

esp32i2cPins = {'sda': 23, 'scl': 22}
frequency=100000

sclPin=esp32i2cPins['scl']
sdaPin=esp32i2cPins['sda']
i2c = I2C(scl=Pin(sclPin), sda=Pin(sdaPin), freq = frequency)

import motor
import time

motors = motor.DCMotors(i2c)

motors.speed(2,2000)
motors.speed(3,2000)

time.sleep(2)

motors.brake(2)
motors.brake(3)
```
