# Martin Jerry MJ-ST02 3-Way Switch ESPHome Configuration

This is a modern, functional ESPHome configuration for the Martin Jerry MJ-ST02 in-wall 3-way Smart switch. [Link to Amazon page](https://www.amazon.ca/dp/B0BJ9D1NM1).

Download binaries at the latest release: <a href="https://github.com/joshuaboniface/martinjerry-esphome/releases"><img alt="GitHub Release" src="https://img.shields.io/github/v/release/joshuaboniface/martinjerry-esphome"></a>

## Motivations

The original YAML config from [ESPHome Devices](https://devices.esphome.io/devices/MJ-ST02) is OK as a start, but I wanted to ensure optimal configuration similar to my SD01 configuration, so I created this too.

## Key Features

* The config is normalized for recent (2025+) ESPHome versions, including an easier setup process. A pre-built binary in AP mode is available, ready to be flashed with `esptool` and adopted easily by HomeAssistant (see below).

## Installing

I got the Tasmota version of this switch, so upgrading was easy over the air. Simply download the compressed binary (`mj-st02.bin.gz`) and upload it via the Tasmota WebUI following [the process here](https://esphome.io/guides/migrate_sonoff_tasmota.html). If you want to compile it yourself, you can do so and then compress the resulting binary file with `gzip`, or alternatively install the [minimal Tasmota build](http://ota.tasmota.com/tasmota/release/tasmota-minimal.bin.gz) first to free up space, then install the uncompressed binary.

## Reporting Bugs or Feature Requests

If you find a bug, please report it by opening an issue.

This device is basic enough that I don't think there's many features to add, but if you come up with one, I'm happy to review it.

## Entities

<p><img alt="Controls entities" src="https://raw.githubusercontent.com/joshuaboniface/martinjerry-esphome/refs/heads/master/mj-s01/images/device.png"/><br/>
<i>Main device information.</i>
</p>
<p><img alt="Controls entities" src="https://raw.githubusercontent.com/joshuaboniface/martinjerry-esphome/refs/heads/master/mj-s01/images/controls.png"/><br/>
<i>Controls entities.</i>
</p>
<p><img alt="Sensors entities" src="https://raw.githubusercontent.com/joshuaboniface/martinjerry-esphome/refs/heads/master/mj-s01/images/sensors.png"/><br/>
<i>Sensors entities.</i>
</p>
<p><img alt="Diagnostic entities" src="https://raw.githubusercontent.com/joshuaboniface/martinjerry-esphome/refs/heads/master/mj-s01/images/diagnostic.png"/><br/>
<i>Diagnostic entities, including reboot and factory reset if required.</i>
</p>

