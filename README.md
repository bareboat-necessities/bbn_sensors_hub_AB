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
- Water quality sensor
- Liquid level (0-20 mAmps)


## Other Bareboat Necessities Devices

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

