# Martin Jerry MJ-ST01 Switch ESPHome Configuration

This is a modern, functional ESPHome configuration for the Martin Jerry MJ-ST01 in-wall 3-Way Smart switch. [Link to Amazon page](https://www.amazon.ca/dp/B0852SY3WH).

Download binaries at the latest release: <a href="https://github.com/joshuaboniface/martinjerry-esphome/releases"><img alt="GitHub Release" src="https://img.shields.io/github/v/release/joshuaboniface/martinjerry-esphome"></a>

## Motivations

There was no good YAML config for this device, as the one on [ESPHome Devices](https://devices.esphome.io/devices/MJ-ST01) similar to this is more like the [MJ-ST02](/mj-st02) with a Tuya MCU rather than this which is a direct relay/LED connection.

## Key Features

* The config is normalized for recent (2025+) ESPHome versions, including an easier setup process. A pre-built binary in AP mode is available, ready to be flashed with `esptool` and adopted easily by HomeAssistant (see below).

* Aside from the naming it is functionally identical to the [MJ-S01 config](/mj-s01).

## Installing

As of my purchase of 3 units [from Amazon](https://www.amazon.ca/dp/B0852SY3WH) in March 2025, `tuya-convert` seems like the most reliable option; it worked perfectly on the first try, though future revisions might not work any longer.

0. Install `tuya-convert` following their instructions.

1. Download the `mj-st01.bin` file from the Releases section, or compile the configuration yourself.

2. Put the `mj-st01.bin` binary into your `tuya-convert/files/` directory.

3. Power on the switch and put it in "fast blink" mode by holding down the power button for ~5 seconds.

4. Run `./start_flash.sh` and let it perform the initial jailbreak.

5. When prompted "Ready to flash third party firmware!", select the `mj-st01.bin` file.

Once flashed, the switch will boot into AP mode, ready to be configured via another device to connect to your WiFi and be adopted by the ESPHome Builder in Home Assistant. It leverages a standard "pull the remote config" to permit configuring only the minimum required in the ESPHome Builder, while all functionality is managed by this repository.

## Reporting Bugs or Feature Requests

If you find a bug, please report it by opening an issue.

This device is basic enough that I don't think there's many features to add, but if you come up with one, I'm happy to review it.

## Entities

<p><img alt="Controls entities" src="https://raw.githubusercontent.com/joshuaboniface/martinjerry-esphome/refs/heads/master/mj-st01/images/device.png"/><br/>
<i>Main device information.</i>
</p>
<p><img alt="Controls entities" src="https://raw.githubusercontent.com/joshuaboniface/martinjerry-esphome/refs/heads/master/mj-st01/images/controls.png"/><br/>
<i>Controls entities.</i>
</p>
<p><img alt="Sensors entities" src="https://raw.githubusercontent.com/joshuaboniface/martinjerry-esphome/refs/heads/master/mj-st01/images/sensors.png"/><br/>
<i>Sensors entities.</i>
</p>
<p><img alt="Diagnostic entities" src="https://raw.githubusercontent.com/joshuaboniface/martinjerry-esphome/refs/heads/master/mj-st01/images/diagnostic.png"/><br/>
<i>Diagnostic entities, including reboot and factory reset if required.</i>
</p>

