# Nissan-Leaf-ChargeCurrent
Software for adjusting AC charge speed on the fly.

Current state of the software: 
* Outputs the max AC charge power via USB. This can be read with e.g. Termite.
* Hardcoded to limit AC charging to an configurable value (3.3 / 1.6kW) Select before compiling

Long term vision: When car is slowcharging, it should be possible to turn down the charge speed using the HVAC controls. This can easily be achieved with the fan controls, simply check if some condition is present (Car is charging && HVAC recirc is ON && FAN speed is MAX), and then go into a setting menu, where tuning down the fan will also tune down the charge current. Very important to only go DOWN, since going up can damage electrical installations. The AMP setting can be visualized with the SOC% on the dashboard.

## How to take software into use
* Download the muxsan repository: https://bitbucket.org/emile_nijssen/open-source-can-bridge/src/master/ 
* Replace the _can-bridge-firmware.c_ file with the one found from this repository
* Compile with Atmel Studio 7, and flash the firmware onto a 3-port CAN bridge
* Install the CAN-bridge onto the EV-CAN of your Nissan LEAF, installation tips found here: https://www.youtube.com/watch?v=eLcNSo2Vn6U
* Enjoy being able to control the charge speed
