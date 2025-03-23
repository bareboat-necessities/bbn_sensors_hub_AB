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

- Lightning strike detector AS3935: https://www.dfrobot.com/product-1828.html
- Barometer via i2c DPS310: https://www.adafruit.com/product/4494 (DPS310 on the picture but several others are supported by firmware too)   
- Temperature/Humidity SHTC3: https://www.aliexpress.us/item/3256807428285646.html (SHTC3 as pictured but others SHT30, DHT12, some more supported by firmware too)
- Multiple 1-wire waterproof temperature probes DS18B20: https://gikfun.com/products/gikfun-ds18b20-waterproof-digital-temperature-sensor-with-adapter-module-for-arduino-pack-of-3-sets (via DS18B20 with GikFun plugin terminal board)
- Illuminance M5Stack DLight (Connected via i2c outside of the box)
- Motion detector PIR Unit from m5stack (Connected outside of the box)
- Hatch open/closed limit switch sensor (Limit Switch Unit from m5stack connected outside of the box)
- i2c connector for more external i2c sensors supported by the Hub A firmware

For all supported hardware and software of Hub A firmware look here:   https://github.com/bareboat-necessities/bbn_sensors_hub_A


## Liquid Levels and Electrical Sensors (Hub B)

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

