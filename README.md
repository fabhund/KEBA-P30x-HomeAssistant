# KEBA-P30x-HomeAssistant
Controls the Keba P30x EV wall-charger in HomeAssistanst. Using ModBus over TCP (LAN connection).

Using the build-in ModBus over TCP in HomeAssistant, this enables you to read all sensors, and set paramanters.
This covers most of the sensors, (error and fault codes are omitted) but you can easily add them.

# HACS Install
Not supported

# Manual install

## Wall box
1. Open up the wall box, and connect a standard LAN cable to your home network
2. Set the DIP-switch 1.3 = ON to enable "Smart communication" (consult your manual)
3. Admin credentials are located, on a label, inside the lid of the protection cover for the LAN and DIP-switched compartment.
4. Access the wall box website, default IP: 192.168.42.1 and login with Admin credentials. Once you have access, you can change it to DHCP, or setting a fixed IP, matching your home network.
5. Restart the wall box. Done.



## HomeAssistant
Here you need to set the following up:
1. Configuration.yaml
2. Create a helper: Input.select (Dropdown style)
3. Automation.yaml
4. Setting up UI


### Configuration.yaml
1. Copy paste the modbus section, template sensors and switches to your existing configuration.yaml
2. Edit the IP:address to the wall Box IP.

### Helper
Create a dropdown helper (input.select" type with the following values
"6 A, 7 A, 8 A, ... 16 A" or whatever your prefer as intervals for setting the charge current

### Automation.yaml
To write values to the wall box (Like max. charge current), create an automation that triggers on the state change (from the helper) when the helper changes state, write the change.
Create a new automation and copy/paste the automation.yaml

# Registers
Registers starting with:
- 1xxx are Read-Only
- 5xxx are Write-Only

Address | Platform | Description | Unit | Device | State
-- | -- | -- | -- | -- | --
5014 | sensor | L1-N Voltage | V | Ampere | measurement
5016 | button | Text sensor for showing cable states in plain text ldfkjg lkfdjg dlkfg lkdjf glkdjfg lkdjgf ldjgf ldkfjg  | - | - | - 
5018 | binary sensor | Text sensor for showing charging states in plain text | - | - | - 

# Volkswagen We Connect ID [ONLY FOR EUROPE]
_Volkswagen We Connect ID sensor provides statistics from the Volkswagen ID Api thru [WeConnect-python lib](https://pypi.org/project/weconnect/)._

**This component will set up the following platforms.**

Platform | Description
-- | --
`sensor` | Show information from your Volkswagen ID car.
`button` | Start climatization in your Volkswagen ID car.

![image](https://user-images.githubusercontent.com/15835274/149675681-a0c6804c-3179-4fd3-ad74-ab489c8986dd.png)


## Installation

### HACS
The easiest way to add the component to your Home Assistant installation is
using [HACS](https://hacs.xyz). Add this GitHub repository as a [custom
repository](https://hacs.xyz/docs/faq/custom_repositories), then follow the
instructions under [Configuration](#configuration) below.

### Manual

1. Using the tool of choice open the directory (folder) for your HA configuration (where you find `configuration.yaml`).
2. If you do not have a `custom_components` directory (folder) there, you need to create it.
3. In the `custom_components` directory (folder) create a new folder called `volkswagen_we_connect_id`.
4. Download _all_ the files from the `custom_components/volkswagen_we_connect_id/` directory (folder) in this repository.
5. Place the files you downloaded in the new directory (folder) you created.
6. Follow the instructions under [Configuration](#configuration) below.

Using your HA configuration directory (folder) as a starting point you should now also have this:

```text
custom_components/volkswagen_we_connect_id/__init__.py
custom_components/volkswagen_we_connect_id/manifest.json
custom_components/volkswagen_we_connect_id/sensor.py
.. etc
```
