# PyGauge
PyGauge is a Python service (also available as a pre-built exe, see [releases](https://github.com/tridento/pygauge/releases/latest)) and accompanying Arduino sketch to display DiRT Rally, DiRT Rally 2.0, DiRT 4 telemetry data (currently gear, speed, and rev lights) on the TM1638 LED module.

## Prerequisites
Instructions assume that you have an Arduino connected via USB serial that you can upload sketches to, and that is hooked up to the TM1638 LED module.

## Install
1. Download the latest [gauge.zip file release](https://github.com/tridento/pygauge/releases/latest)
2. Download the [TM1638 library](https://code.google.com/p/tm1638-library/) and place in your Arduino libraries directory.
3. Download the [arduino sketch](arduino/tm1638-gauge.ino), update the pin values for strobe, clock and data pins, and upload your sketch.
4. Update your DiRT Rally (DiRT 4, DiRT Rally 2.0) hardware_settings_config (located in `<user>\Documents\My Games\DiRT Rally\hardwaresettings` (or another game folder), setting motion_platform > udp `enabled` to true, and `extradata` to 3.
```xml
<motion_platform>
  ...
  <udp enabled="true" extradata="3" ip="127.0.0.1" port="20777" delay="1" />
</motion_platform>
```
5. Update the `config.yml` file in the gauge.zip, setting the port and ip address to match information above, and the COM port your arduino is connected to.
6. Run `gauge.exe` and launch the game. If everything's set up correctly, you should begin to see telemetry information when your stage begins.

## Building / Contributing

Assuming you're running in a git bash / cygwin / etc environment:

1. Install python dependencies with `pip install -r requirements.txt`
2. Run `build.sh`

This will build an exe and copy the config file in the `dist` directory, and create a zip containing these files.

## Fork Notes
Oh. I have just updated it to work with Python 3 and other Codemasters games like D4, Grid Autosport, Dirt Rally 2.0. Still no luck to get it working with D2, D3, havent tested it with F1 games.
