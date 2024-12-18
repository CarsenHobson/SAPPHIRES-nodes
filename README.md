Overview

This repository contains Python scripts for interfacing with air quality sensors (SPS30 and BME280) and a Raspberry Pi, using MQTT for communication. The scripts monitor air quality parameters, manage sensor operation, and provide mechanisms for device control, including system reboot functionality.

Features
	1.	Air Quality Data Collection:
	•	Measures PM2.5, temperature, and humidity using the SPS30 and BME280 sensors.
	•	Converts temperature readings from Celsius to Fahrenheit.
	•	Logs data locally and publishes it to an MQTT broker.
	2.	Wi-Fi Signal Strength Monitoring:
	•	Retrieves and calculates Wi-Fi signal strength in percentage.
	3.	MQTT Communication:
	•	Publishes air quality and Wi-Fi strength data to an MQTT topic.
	•	Subscribes to an MQTT topic to listen for remote commands (e.g., system reboot).
	4.	Sensor Control:
	•	Scripts to start and stop SPS30 measurements.
	5.	System Reboot:
	•	Listens for a “reboot” command via MQTT and reboots the system upon receipt.

 Prerequisites
	•	Hardware:
	•	Raspberry Pi with Python 3 installed.
	•	SPS30 particulate matter sensor.
	•	BME280 temperature and humidity sensor.
	•	Python Libraries:
	•	paho-mqtt
	•	smbus2
	•	bme280
	•	sps30
	•	subprocess
	•	logging

 File Descriptions

1. air_quality_monitor.py
	•	Purpose:
	•	Measures air quality data (PM2.5, temperature, humidity) and Wi-Fi strength.
	•	Publishes sensor data to the MQTT broker.
	•	Key Functions:
	•	celsius_to_fahrenheit(celsius): Converts temperature to Fahrenheit.
	•	get_wifi_strength(): Retrieves Wi-Fi signal strength as a percentage.
	•	MQTT Topic: ZeroW2.

2. mqtt_reboot_listener.py
	•	Purpose:
	•	Subscribes to the Reset2 MQTT topic.
	•	Reboots the system if the message “reboot” is received.
	•	MQTT Topic: Reset2.

3. start_sps30.py
	•	Purpose:
	•	Starts SPS30 measurement.
	•	Function:
	•	start_sps30(): Initiates SPS30 operation.

4. stop_sps30.py
	•	Purpose:
	•	Stops SPS30 measurement.
	•	Function:
	•	stop_sps30(): Halts SPS30 operation.

Setup Instructions
1.	Install Required Libraries:
   pip install paho-mqtt smbus2 sps30

2.	Connect Hardware:
	•	Wire the SPS30 and BME280 sensors to the Raspberry Pi.
	•	Ensure the I2C interface is enabled on the Raspberry Pi.
3.	Configure MQTT Broker:
	•	Set up an MQTT broker (e.g., Mosquitto) at the IP address specified in the scripts (10.42.0.1).
4.	Run Scripts:
	•	Execute air_quality_monitor.py to start monitoring and publishing sensor data.
	•	Use mqtt_reboot_listener.py to listen for reboot commands.
5.	Start/Stop SPS30 Manually:
	•	Run start_sps30.py or stop_sps30.py as needed.

Logging
	•	Logs are saved in /home/zerow1/logfile.log.
	•	Errors and events such as failed Wi-Fi strength retrieval or sensor initialization issues are logged for troubleshooting.

 	
