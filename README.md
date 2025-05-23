# bbn_sensors_hub_AB
BBN NMEA XDR sensors hub esp32 hardware 

<p align="center">
<img src="./img/bbn_boat_sensors_hubAB_notes.jpg?raw=true" style="width: 75%; height: auto;" alt="BBN HubAB pic1" />
</p>

<p align="center">
<img src="./img/bbn_boat_sensors_hubAB_2.jpg?raw=true" style="width: 40%; height: auto;" alt="BBN HubAB pic3" />
<img src="./img/bbn_boat_sensors_hubAB_3.jpg?raw=true" style="width: 40%; height: auto;" alt="BBN HubAB pic2" />
</p>

<p align="center">
<img src="./img/bbn_boat_sensors_hubAB_5.jpg?raw=true" style="width: 40%; height: auto;" alt="BBN HubAB pic5" />
<img src="./img/bbn_boat_sensors_hubAB_10.jpg?raw=true" style="width: 40%; height: auto;" alt="BBN HubAB pic4" />
</p>

## Hardware

It's really two devices in one. Both use __atomS3-lite__ esp32s3 microcontroller from m5stack: https://shop.m5stack.com/products/atoms3-lite-esp32s3-dev-kit

Hub A is mostly environental sensors:

- Lightning strike detector
- Pressure
- Temperature/Humidity
- Multiple 1-wire waterproof temperature probes
- Illuminance
- Motion detector
- Hatch open/closed limit switch sensor
- i2c connector for more external i2c sensors supported by the Hub A firmware

Hub B is for electrical and liquid level sensors:

- Current/Voltage/Power sensors
- Resistance sensor for fuel level, engine oil pressure, rudder position, or trim
- Water quality (TDS - Total Dissolved Solids) sensor
- Liquid level (0-20 mAmps)

### Enclosure, etc

- Waterproof box. Hinged with stainless steel hardware, transparent lid, base plate and legs
- Various cable glands
- Grove cables from m5stack
- M3 standoffs
- __In-Sure lever wire connectors__ for splicing wires (3-Port and 5-port): https://www.idealind.com/us/en/category/product.html/In_Sure_Lever_5_Port.html
- Cable ties
- __Grove2Dupont Conversion Cables__: https://shop.m5stack.com/products/grove2dupont-conversion-cable-20cm-5pairs
- USB-C to USB-A cables with small support tang on USB-C end

## Environmental Sensors (Hub A)

- Lightning strike detector __AS3935__: https://www.dfrobot.com/product-1828.html (Placed inside the box)
- Barometer via i2c __DPS310__: https://www.adafruit.com/product/4494 (DPS310 inside the box on the picture but several others are supported by firmware too)   
- Temperature/Humidity __SHTC3__: https://www.aliexpress.us/item/3256807428285646.html (SHTC3 as pictured but others SHT30, DHT12, some more supported by firmware too)
- Multiple 1-wire waterproof temperature probes __DS18B20__: https://gikfun.com/products/gikfun-ds18b20-waterproof-digital-temperature-sensor-with-adapter-module-for-arduino-pack-of-3-sets (via DS18B20 with GikFun plugin terminal board)
- Illuminance __M5Stack DLight BH1750FVI-TR__: https://shop.m5stack.com/products/dlight-unit-ambient-light-sensor-bh1750fvi-tr (Placed and connected via i2c outside of the box)
- Motion detector __M5Stack PIR Unit AS312__: https://shop.m5stack.com/products/pir-module (Placed outside of the box)
- Hatch open/closed limit switch sensor https://shop.m5stack.com/products/limit-switch-unit (__Limit Switch Unit from m5stack__ placed outside of the box)
- i2c connector for more external i2c sensors supported by the Hub A firmware (See: https://github.com/bareboat-necessities/bbn_sensors_hub_A)
- __ATOMIC PortABC Extension Base__ to expose esp32 ports: https://shop.m5stack.com/products/atomic-portabc-extension-base
- __M5Stack 1 to 3 HUB Expansion Unit__: https://shop.m5stack.com/products/mini-hub-module

For all supported hardware and software of Hub A firmware look here:   https://github.com/bareboat-necessities/bbn_sensors_hub_A

### Making Connections for Hub A

For pins used in connections browse through the firmware code: https://github.com/bareboat-necessities/bbn_sensors_hub_A

M5Stack connectors are well color coded and pins are labeled on m5stack portABC.

### Loading Firmware for Hub A

### On Bareboat Necessities (BBN) OS (full)

Long press side button on atomS3 till you see green to enter the mode for uploading firmware.

NOTE: /dev/ttyACM1 in the script below is for example. In your case device name might be different. You can find out what it is by
inspecting differences in output of 

```
ls -ltr /dev/tty*
```

with the device unplugged from USB and plugged into USB.


#### Load the hub A firmware:

````
# shutdown signalk
sudo systemctl stop signalk

if [ -f bbn-flash-sensors-hub-A.sh ]; then rm bbn-flash-sensors-hub-A.sh; fi
wget https://raw.githubusercontent.com/bareboat-necessities/my-bareboat/refs/heads/master/m5stack-tools/bbn-flash-sensors-hub-A.sh
chmod +x bbn-flash-sensors-hub-A.sh 
./bbn-flash-sensors-hub-A.sh -p /dev/ttyACM1
````

Unplug and plug the device into USB to reboot.

### Reading serial port

````
stty -F /dev/ttyACM1 38400
socat stdio /dev/ttyACM1
````




## Liquid Levels and Electrical Sensors (Hub B)

- Current/Voltage/Power __INA219__ sensors: https://www.adafruit.com/product/904 (Two inside the box as on the picture but more are supported by the firmware)
- Water quality __Ocean TDS Total Dissolved Solids sensor__:  https://www.cqrobot.com/index.php?route=product/product&product_id=1122
- Liquid level (0-20 mAmps) __M5Stack Ammeter ADS1115 Unit__ https://shop.m5stack.com/products/ammeter-unit-ads1115 and __Submersible Stainless Steel 0-20 mA Liquid Level Sensor__: https://www.aliexpress.us/item/3256807215987468.html
- Resistive sensors 240-33 ohms or 10-180 ohms for fuel level, engine oil pressure, rudder position, or trim (Not on the picture but supported by Hub B firmware)
- __ATOMIC PortABC Extension Base__ to expose esp32 ports: https://shop.m5stack.com/products/atomic-portabc-extension-base
- __M5Stack 1 to 3 HUB Expansion Unit__: https://shop.m5stack.com/products/mini-hub-module

For all supported hardware and software of Hub B firmware look here:   https://github.com/bareboat-necessities/bbn_sensors_hub_B

### Making Connections for Hub B

For pins used in connections browse through the firmware code: https://github.com/bareboat-necessities/bbn_sensors_hub_B

M5Stack connectors are well color coded and pins are labeled on m5stack portABC.

### Loading Firmware for Hub B

### On Bareboat Necessities (BBN) OS (full)

Long press side button on atomS3 till you see green to enter the mode for uploading firmware.

NOTE: /dev/ttyACM1 in the script below is for example. In your case device name might be different. You can find out what it is by
inspecting differences in output of 

```
ls -ltr /dev/tty*
```

with the device unplugged from USB and plugged into USB.


#### Load the hub B firmware:

````
# shutdown signalk
sudo systemctl stop signalk

if [ -f bbn-flash-sensors-hub-B.sh ]; then rm bbn-flash-sensors-hub-B.sh; fi
wget https://raw.githubusercontent.com/bareboat-necessities/my-bareboat/refs/heads/master/m5stack-tools/bbn-flash-sensors-hub-B.sh
chmod +x bbn-flash-sensors-hub-B.sh
./bbn-flash-sensors-hub-B.sh -p /dev/ttyACM1
````

Unplug and plug the device into USB to reboot.

### Reading serial port

````
stty -F /dev/ttyACM1 38400
socat stdio /dev/ttyACM1
````

## Integration with SignalK

Integration with SignalK is done via NMEA XDR Parser SignalK plugin.

More: https://github.com/GaryWSmith/xdr-parser-plugin

Recommended config file for XDR Parser SignalK plugin:

https://github.com/bareboat-necessities/lysmarine_gen/blob/bookworm/install-scripts/4-server/files/xdrParser-plugin.json

When registering a serial connection in SignalK use device symbolic link from /dev/serial/by-id/ (instead of direct /dev/ttyXXX name).

## Other Bareboat Necessities Devices

Project Home:  https://bareboat-necessities.github.io/


- Alarms Box: https://github.com/bareboat-necessities/bbn_alarms_A
- Engine Sensors Box: https://github.com/bareboat-necessities/bbn_sensors_hub_C
- NMEA N2K to USB: https://github.com/bareboat-necessities/bbn-m5-s3-n2k-usb
- Instruments Displays on esp32: https://github.com/bareboat-necessities/bbn-m5stack-tough
- Boat Heave Sensor: https://github.com/bareboat-necessities/bbn-wave-period-esp32
- I2C over USB for Linux: https://github.com/bareboat-necessities/bbn-i2c-over-usb
- N2K Senders: https://github.com/bareboat-necessities/bbn-m5-s3-n2k-i2c


