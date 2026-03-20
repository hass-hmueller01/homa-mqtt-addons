# Home Assistant add-on: HomA MQTT APsystems EZ1 <!-- omit from toc -->

This add-on is a bridge from [APsystems](https://apsystems.com/) EZ1 inverter local API to [HomA](https://github.com/binarybucks/homA) MQTT framework.

- [Acknowledgements](#acknowledgements)
- [Installation](#installation)
- [How to use](#how-to-use)
- [Configuration](#configuration)
- [Internal documentation](#internal-documentation)
  - [APsystems-EZ1-mqtt configuration](#apsystems-ez1-mqtt-configuration)
  - [ECU](#ecu)
  - [MQTT](#mqtt)
  - [Timezone](#timezone)
  - [MQTT topics](#mqtt-topics)
  - [Development maintainance](#development-maintainance)


## Acknowledgements

This work is based on [aps2mqtt (v1.2.0)](https://github.com/fligneul/aps2mqtt). Thanks for your work [Florian L.](https://github.com/fligneul)! And thanks for the permission to switch to MIT license.

## Installation

The access to the local API of the APsystems EZ1 inverter is done by the [APsystems-EZ1-API](https://github.com/SonnenladenGmbH/APsystems-EZ1-API) documentation. Please follow the step by step instructions there.

All relevant settings are done in the add-on Configuration page (see also [Configuration](#configuration)).

## How to use

Configure and start the add-on. That's all.

To remove all retained MQTT messages from the broker, you can use
```shell
$ ssh root@homeassistant
$ docker exec -it _container_name_ /bin/bash # _container_name_ see docker ps
$ cd /etc/services.d/apsystems-ez1
$ source .venv/bin/activate
$ python -m apsystems_ez1_mqtt -r
```

## Configuration

The add-on supports the internal (Home Assistant) or an external MQTT broker. To configure the external MQTT broker you have to activate the _"Show unused optional configuration options"_.

You need to set the _"APsystems ECU IP"_ on which the APsystems-EZ1-API can be accessed.

The settings for `APS_ECU_TIMEZONE`, `APS_ECU_POSITION_LAT` and `APS_ECU_POSITION_LNG` are querried from the Home Assistant core API (see Settings > System > Home information > Location / Region).

The _"Update Interval"_ should be not lower than 10s.

## Internal documentation

### APsystems-EZ1-mqtt configuration

APsystems-EZ1-mqtt configuration can be provided by a yaml config file or by environment variables (in a container context for example).

Using the yaml config you can copy provided template `config-template.yaml` e.g. to `config.yaml`.

Config at least the IP of the APsystems EZ1 inverter (`APS_ECU_IP`) and the MQTT broker settings (`MQTT_BROKER_*`).

If you do not need the [HomA](https://github.com/binarybucks/homA) environment you can set `HOMA_ENABLED: False`.

If you do not need [Home Assistant](https://www.home-assistant.io) you can set `HASS_ENABLED: False`.

### ECU

| Key | Description | Example | Default value |
|:----|:------------|:--------|:--------------|
| APS_ECU_IP | IP of the ECU | "192.168.0.42" | None, this field id mandatory |
| APS_ECU_PORT | Communication port of the ECU | 8050 | 8050 |
| APS_ECU_UPDATE_INTERVAL | Time between the update polls | 60 | 15 |
| APS_ECU_STOP_AT_NIGHT | Stop ECU query during the night | True | False |
| APS_ECU_POSITION_LAT | Latitude of the ECU, used to retrieve sunset and sunrise <br />:information_source: Only used if stop at night is enabled | 51.49819 | 52.5162 (Berlin) |
| APS_ECU_POSITION_LNG | Longitude of the ECU, used to retrieve sunset and sunrise <br />:information_source: Only used if stop at night is enabled | -0.13087 | 13.3777 (Berlin) |
| APS_ECU_TIMEZONE | Timezone of the ECU | "Europe/Berlin" | None (use system timezone) |

### MQTT

| Key | Description | Example | Default value |
|:----|:------------|:--------|:--------------|
| MQTT_BROKER_HOST | Host of the MQTT broker | "broker.hivemq.com" | "127.0.0.1" |
| MQTT_BROKER_PORT | Port of the MQTT broker | 8883 | 1883 |
| MQTT_BROKER_USER | User login of the MQTT broker | "john-deere" | "" |
| MQTT_BROKER_PASSWD | User password of the MQTT broker | "secret" | "" |
| MQTT_BROKER_SECURED_CONNECTION | Use secure connection to MQTT broker | True | False |
| MQTT_BROKER_CACERTS_PATH | Path to the cacerts file | "/home/jd/.ssl/cacerts" | None |
| MQTT_CLIENT_ID | Client ID if the MQTT client | "foo" | "" |
| MQTT_TOPIC_PREFIX | Topic prefix for publishing <br />:information_source: Only used if HomA is disabled | "/aps/" | "" |
| |
| HOMA_ENABLED| Enable HomA MQTT messages | False | True |
| HOMA_SYSTEMID| HomA system id <br />:information_source: Use inverter id if empty | "123456-solar" | '' |
| HOMA_ROOM| HomA room to show data | "PV" | "Sensors" |
| HOMA_NAME| HomA name | "My PV System" | "Solar PV" |
| |
| HASS_ENABLED| Enable Home Assistant MQTT messages | True | False |
| HASS_DEVICE_ID| Home Assistant id <br />:information_source: Use inverter id if empty |  | "" |
| HASS_DEVICE_NAME| Home Assistant device name | "Solar PV Balkonkraftwerk" | "Solar PV" |
| HASS_NAME_PREFIX| Home Assistant name prefix | "Solar " | "" |
| HASS_AREA| Home Assistant area name | "My PV System" | "Energie" |

### Timezone

Without any specific configuration, APsystems-EZ1-mqtt uses your system's timezone as a reference.

* It is recommented setting the timezone by the configuration variable `APS_ECU_TIMEZONE` for better processing.
* Alternatively, if set, the environement variable `TZ` is used.

### MQTT topics

The APsystems-EZ1-mqtt topics depend on the configuration. If HomA is deactivated (`HOMA_ENABLED: False`) topics start with [MQTT_TOPIC_PREFIX], otherwise "/devices/[HOMA_SYSTEMID]/controls/" will be used.

* [topic start]Power - total amount of power (in W) being generated right now
* [topic start]Power P1 - power of channel 1 (in W) being generated right now
* [topic start]Power P2 - power of channel 2 (in W) being generated right now
* [topic start]Energy today - total amount of energy (in kWh) generated today
* [topic start]Energy today P1 - channel 1 amount of energy (in kWh) generated today
* [topic start]Energy today P2 - channel 2 amount of energy (in kWh) generated today
* [topic start]Energy lifetime - total lifetime amount of energy (in kWh) generated
* [topic start]Energy lifetime P1 - channel 1 lifetime amount of energy (in kWh) generated
* [topic start]Energy lifetime P2 - channel 2 lifetime amount of energy (in kWh) generated

If Home Assistant is enabled (`HASS_ENABLED: True`) Home Assistant auto config messages will be generated, like: "homeassistant/sensor/[object_id]/config"

### Development maintainance

To update the dependencies of an existing `.venv` Python environment during development execute the following commands
```shell
cd apsystems-ez1-homa/rootfs/etc/services.d/apsystems-ez1
source .venv/bin/activate
poetry show -o
poetry update
```
