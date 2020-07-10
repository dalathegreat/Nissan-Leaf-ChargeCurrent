# Nissan-Leaf-ChargeCurrent
Software for adjusting charge speed on the fly

Current state of the software:
It will output the charge current via USB. This can be read with e.g. Termite. This will be useful information for how to interpret this value better.

Long term vision:
When car is slowcharging, it should be possible to turn down the charge speed using the HVAC controls. This can easily be achieved with the fan controls, simply check if some condition is present (Car is charging && HVAC recirc is ON && FAN speed is MAX), and then go into a setting menu, where tuning down the fan will also tune down the charge current. Very important to only go DOWN, since going up can damage electrical installations. The AMP setting can be visualized with the SOC% on the dashboard.
