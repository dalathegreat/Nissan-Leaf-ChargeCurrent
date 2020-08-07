# Nissan-Leaf-ChargeCurrent
Adjusting AC max charge speed is something that most EV makers have on their vehicles. This setting is ofter accessed via a touchscreen inside the vehicle. Unfortunately, the Nissan Leaf is not equipped with this setting, even though the on-board-charger is technically able to decide what amount of power can go into the battery. This has led owners of the Leaf to rely on the EVSE to set the correct max power lever. Often leading to the user having to opt for a more expenive EVSE that has some current control on the cable/handle. The code here aims to correct this, and enable setting the charge speed from within the vehicle.

Current state of the software: 
* Outputs the max AC charge power via USB. This can be read with e.g. Termite.
* 7 different steps of adjustability (Unrestricted/6/5/4/3/2/1)kW

## How to tune the max kW setting
When the car is connected to an EVSE and is slowcharging, turn on the car to wake up the HVAC controls. Set the fan to maximum speed(7), and switch on recirculation mode. You will see the capacity bars on the dash board start to move, along with the SOC% if you have the newer LEAF that has this. These are the current options
Condition held:
<4s - Unrestricted kW, 12bars, SOC%=66
>4s - 6.0kW, 11bars, SOC%=60
>6s - 5.0kW, 10bars, SOC%=50
>8s - 4.0kW, 9bars, SOC%=40
>10s - 3.0kW, 8bars, SOC%=30
>12s - 2.0kW, 7bars, SOC%=20
>14s - 1.0kW, 6bars, SOC%=10

## I want this! How do I get started?
* Download the muxsan repository: https://bitbucket.org/emile_nijssen/open-source-can-bridge/src/master/ 
* Replace the _can-bridge-firmware.c_ file with the one found from this repository
* Compile with Atmel Studio 7, and flash the firmware onto a 3-port CAN bridge
* Install the CAN-bridge onto the EV-CAN of your Nissan LEAF, installation tips found here: https://www.youtube.com/watch?v=eLcNSo2Vn6U
* Enjoy being able to control the charge speed
