# Martin Jerry MJ-S01 Switch ESPHome Configuration

This is a modern, functional ESPHome configuration for the Martin Jerry MJ-S01 in-wall Smart switch. [Link to product page](https://www.martinjerry.com/product-page/smart-non-dimmer-switch-single-pole-model-us-s01). [Link to Amazon page](https://www.amazon.ca/dp/B07C235D9G).

Download binaries at the latest release: <a href="https://github.com/joshuaboniface/martinjerry-esphome/releases"><img alt="GitHub Release" src="https://img.shields.io/github/v/release/joshuaboniface/martinjerry-esphome"></a>

**Note**: I was quite confused myself as to whether this is an "S01" with a newer chip and relay, or an "SS01". [The ESPHome Devices database](https://github.com/esphome/esphome-devices) contains entries for both, and my GPIO pins matched the "S01", so I've gone with that name. Your millage may vary.

## Motivations

The original YAML config from [ESPHome Devices](https://devices.esphome.io/devices/MJ-S01) is OK as a start, but I wanted to ensure optimal configuration similar to my SD01 configuration, so I created this too.

## Key Features

* The config is normalized for recent (2025+) ESPHome versions, including an easier setup process. A pre-built binary in AP mode is available, ready to be flashed with `esptool` and adopted easily by HomeAssistant (see below).

## Installing

As of my purchase of 2 units [from Amazon](https://www.amazon.ca/dp/B07C235D9G) in March 2025, **none of the normal Tuya jailbreak mechanisms worked**. This was unfortunate, and means that more intrusive measures were needed.

The switch is fairly easy to open, using a thin spudger to pop off the case from one side. There is no longer a wheel to worry about so it should pop right off.

Once inside, the chip is a CB3S running Tuya 1.3.5 firmware, with no obvious OTA jailbreak method. I also tried direct serial flashing, but this would just return error after error.

At that point I decided that the easiest, and best long-term, solution was to simply replace the CB3S with an actual ESP8266 12-E/F module. Using a heat gun, I desoldered the module from a spare NodeMCU I had lying around, removed the CB3S module from the control board of the switch, and then replaced it with the ESP8266 module. This took about 5 minutes total and was not particularly daunting, as the positioning of the components on the switch board is quite generous to avoid stray heat issues; watch the wires out the back though!

From there, I flashed the ESP8266 with this configuration via TTL serial, though you could of course do it in the opposite order if you wish. I still provide a binary release that can be flashed directly via `esptool`, or you can use `esphome` directly with the config while connected via serial.

1. Download the `mj-s01.bin` file from the Releases section, or compile the configuration yourself.

2. Connect your ESP8266 chip via a serial TTL cable [via the following pins](https://randomnerdtutorials.com/esp8266-pinout-reference-gpios/):

   * VCC & GND to their respective pins
   * TXD01 to RX and RXD01 to TX
   * GPIO0 to GND

3. Run the flash with `esptool.py` (or via `esphome run`): `esptool.py --before default_reset --after hard_reset --baud 460800 --port /dev/ttyUSB0 --chip esp8266 write_flash -z --flash_size detect 0x0 mj-s01.bin`

4. Disconnect GPIO0 and reset the switch (power or reset button).

Once flashed, the switch will boot into AP mode, ready to be configured via another device to connect to your WiFi and be adopted by the ESPHome Builder in Home Assistant. It leverages a standard "pull the remote config" to permit configuring only the minimum required in the ESPHome Builder, while all functionality is managed by this repository.

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

