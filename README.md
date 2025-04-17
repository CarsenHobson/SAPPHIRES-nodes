This repository contains all of the code the for the outdoor nodes for the SAPPHIRES project

The main code is the zerow script which reads data from the sensors and then sends it over MQTT to the central hub

There are also the startsps30 and stopsps30 that are essential to be implemented correctly in the cronjob so that the sps30 is reset every twelve hours.

The last script is the ZeroWreboot code that receives a signal from the central hub in case it determines that the node needs to be reset by turning it on and off. This function is slightly incomplete at the moment and has not been integrated into the current central hub setup.

The cronjob is also contained in this repository
