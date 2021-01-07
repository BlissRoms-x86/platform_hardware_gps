# Android Serial GPS Driver

Generic Android driver for serial and USB(-to-serial) GPS receivers that use the [NMEA](https://en.wikipedia.org/wiki/NMEA_0183) or [UBX](https://www.google.com/search?q=u-blox+ubx+protocol) protocol. 

## How to use

This driver is included by default with Bliss OS and can be enabled by editing your [build.prop](a "The platform configuration file") with a text editor (or another suitable tool such as [BuildProp Editor](https://www.google.com/search?q=buildprop+editor)) and adding the configuration lines in the table below in the format `key=value`

Key | Value | Required | Purpose
-|-|-|-
**ro.kernel.android.gps** | ttyUSB0 | **Yes** | The *TTY* of your GPS receiver, such as ttyUSB0, ttyS0, ttyO1 etc
**ro.kernel.android.gpsttybaud** | 9600 | No | The *baud rate* of your GPS receiver, if not specified this defaults to 9600 (baud)
**ro.kernel.android.gps.max_rate** | 1 | No | **For u-blox receivers only**, this is the poll rate in *seconds* if between 1..65, otherwise *milliseconds* if between 250..65000, defaults to 1 (second), recommended value is no faster than 500 (milliseconds)
**ro.kernel.android.gps.time_sync** | 0 | No | Number of *seconds* drift between system and GPS clocks before driver synchronizes system time with GPS time, recommended value here is 20-30 seconds, a value of 0 (the default) disables this feature

## Known-working devices
This is a list of devices that have been confirmed working by Bliss staff.

GPS Receiver | Platforms | TTY | Baud | Works out the box? | Comments
-|-|-|-|-|-
GlobalSat BU-353 S4 USB Receiver | i3-330M Laptop, LattePanda v1 and Intel Joule 570X | ttyUSB0 | 4800 | Yes | 
Telit SE868 v2 USB Receiver | LattePanda v1 | ttyUSB0 | 9600 | Yes |
Adafruit Ultimate GPS Breakout v3 via Raspberry Pi TTL to USB cable | LattePanda v1 and Intel Joule 570X | ttyUSB0 | 9600 | Yes |
Adafruit Ultimate GPS Breakout v3 via UART | Intel Joule 570X | ttyS1 |9600 | Yes | Connect TX pin on GPS to Joule pin B1_24
## Notes

* If using a USB device make sure you have the necessary kernel modules loaded or built in to the kernel.
* Make sure the permissions on your device file are correct

## Contributors

This driver was originally developed by [Chih-Wei Huang](https://github.com/cwhuang) and then further developed by [Keith Conger](https://github.com/kconger) who included this message with his code:

```
If you find any of this useful and want to show appreciation see below:

PayPal: keith.conger@gmail.com
Bitcoin: 1Pg54vVnaLxNsziA6cy9CTefoEG5iAm9Uh
```

Other contributors include:

**Upstream**

* [dipcore](https://github.com/dipcore)
* [Steven Joruk](https://github.com/steven-joruk)
* [Martin Kolaci](https://github.com/Martin-Kolaci)

**Bliss**

* [Jon West](https://github.com/electrikjesus)
* [Jason Gaunt](https://github.com/jasongaunt)