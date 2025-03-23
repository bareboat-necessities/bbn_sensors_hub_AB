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

It's really two devices in one. Both use atomS3-lite esp32s3 microcontroller from m5stack.

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

## Environmental Sensors (Hub A)

- Lightning strike detector __AS3935__: https://www.dfrobot.com/product-1828.html
- Barometer via i2c __DPS310__: https://www.adafruit.com/product/4494 (DPS310 inside the box on the picture but several others are supported by firmware too)   
- Temperature/Humidity __SHTC3__: https://www.aliexpress.us/item/3256807428285646.html (SHTC3 as pictured but others SHT30, DHT12, some more supported by firmware too)
- Multiple 1-wire waterproof temperature probes __DS18B20__: https://gikfun.com/products/gikfun-ds18b20-waterproof-digital-temperature-sensor-with-adapter-module-for-arduino-pack-of-3-sets (via DS18B20 with GikFun plugin terminal board)
- Illuminance __M5Stack DLight BH1750FVI-TR__: https://shop.m5stack.com/products/dlight-unit-ambient-light-sensor-bh1750fvi-tr (Placed and connected via i2c outside of the box)
- Motion detector __M5Stack PIR Unit AS312__: https://shop.m5stack.com/products/pir-module (Placed outside of the box)
- Hatch open/closed limit switch sensor https://shop.m5stack.com/products/limit-switch-unit (__Limit Switch Unit from m5stack__ placed outside of the box)
- i2c connector for more external i2c sensors supported by the Hub A firmware (See: https://github.com/bareboat-necessities/bbn_sensors_hub_A)

For all supported hardware and software of Hub A firmware look here:   https://github.com/bareboat-necessities/bbn_sensors_hub_A


## Liquid Levels and Electrical Sensors (Hub B)

- Current/Voltage/Power __INA219__ sensors: https://www.adafruit.com/product/904 (Two inside the box as on the picture but more are supported by the firmware)
- Water quality __Ocean TDS Total Dissolved Solids sensor__:  https://www.cqrobot.com/index.php?route=product/product&product_id=1122
- Liquid level (0-20 mAmps) __M5Stack Ammeter ADS1115 Unit__ https://shop.m5stack.com/products/ammeter-unit-ads1115 and __Submersible Stainless Steel 0-20 mA Liquid Level Sensor__: https://www.aliexpress.us/item/3256807215987468.html
- Resistance sensor 240-33 ohms or 10-180 ohms for fuel level, engine oil pressure, rudder position, or trim (Not on the picture but supported by Hub B firmware)

For all supported hardware and software of Hub B firmware look here:   https://github.com/bareboat-necessities/bbn_sensors_hub_B

## Other Bareboat Necessities Devices

Project Home:  https://bareboat-necessities.github.io/


https://github.com/bareboat-necessities/bbn_alarms_A

Alarm Box A: 

- Bilge level using ultrasonic range sensor
- Battery voltage
- Ethernet interface
- Alarms sent via WhatsApp
- Without alarms configured acts as NMEA XDR sender


Hub C (planned):

- Thermocouple sensor for exhaust temperature
- Engine RPM
- Resistance sensor for fuel level, engine oil pressure, rudder position, or trim
- i2c connector for more external i2c sensors supported by the Hub A firmware

