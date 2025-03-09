# bbn_sensors_hub_AB
BBN NMEA XDR sensors hub esp32 hardware 

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

Hub C (planned):

- Thermocouple sensor for exhaust temperature
- Engine RPM
