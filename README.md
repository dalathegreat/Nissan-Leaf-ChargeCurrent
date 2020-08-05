# Nissan-Leaf-ChargeCurrent
Adjusting AC max charge speed is something that most EV makers have on their vehicles. This setting is ofter accessed via a touchscreen inside the vehicle. Unfortunately, the Nissan Leaf is not equipped with this setting, even though the on-board-charger is technically able to decide what amount of power can go into the battery. This has led owners of the Leaf to rely on the EVSE to set the correct max power lever. Often leading to the user having to opt for a more expenive EVSE that has some current control on the cable/handle. The code here aims to correct this, and enable setting the charge speed from within the vehicle.

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
