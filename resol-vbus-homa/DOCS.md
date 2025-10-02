# Home Assistant add-on: HomA RESOL VBus

This add-on is a RESOL VBus to MQTT bridge used by HomA MQTT framework.

## How to use

Once installed, the plugin fetches data from RESOL VBus and pushes it to the HomA MQTT topics `/devices/<systemID>/controls/<topic>`.

These topics are supported:
- Kollektortemperatur
- Speichertemperatur unten
- Speichertemperatur Mitte
- Ruecklauftemperatur
- Solarpumpe Drehzahl
- Umschaltventil Position
- Solar Zeit

## Configuration

Setup all the needed configuration parameter.

The add-on supports the internal (Home Assistant) or an external MQTT broker. To configure the external MQTT broker you have to activate the _"Show unused optional configuration options"_.

You can modify the subscribed topic id `<systemId>` by setting _"HomA System ID"_.

Note: To use the serial GPIO ports edit the
`/mnt/boot/config.txt` file on your RPi and set
```
enable_uart=1
dtoverlay=uart0-pi5
```
