# KEBA-P30x-HomeAssistant
Controls the Keba P30x EV wall-charger in HomeAssistanst. Using ModBus over TCP (LAN connection).

Using the build-in ModBus over TCP in HomeAssistant, this enables you to read all sensors, and set paramanters.
This covers most of the sensors, (error and fault codes are omitted) but you can easily add them.

# How-to
Open up the chargebox connect LAN cable to your home network
Set the DIP-switch to enable "Smart communication" DIP-Switch 1.3 = ON (consult your manual)
Inside the lid of the protection cover for the LAN and DIP-switched is a label with admin credentials, note them down.
Access the Chargebox website, default IP: 192.168.42.1 If you are on a different sub-net like 192.168.50.x you need to add the other sub-net in your router, or IP v4 setting in you network device.
Once you have access, you can change it to DHCP, or setting a fixed IP, matching your home network.
Restart the box. Done.

# HomeAssistant
Here you need to set the following up:
-Configuration.yaml
-Create a helper: Input.select (Dropdown style)
-Automation.yaml
-Setting up UI


# Configuration.yaml
Copy paste the modbus section, template sensors and switches to your existing configuration.yaml in the correct place.
Edit the IP:adress to the Charge Box IP.

# Helper
Create a dropdown helper (input.select" type with the following values
"6 A, 7 A, 8 A, --- 16 A" or what ever your prefer as intervals for seeting the charge current

# Automation.yaml
In order to write a value to the charger, create an autmation that triggers on the value change (from the helper) when the helper changes state, write the change
Create a new automation and copy/paste the automation.yaml

