# Home Assistant HomA MQTT add-ons repository

[![Open your Home Assistant instance and show the add add-on repository dialog with a specific repository URL pre-filled.](https://my.home-assistant.io/badges/supervisor_add_addon_repository.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https%3A%2F%2Fgithub.com%2Fhass-hmueller01%2Fhoma-mqtt-addons)


## About

Home Assistant allows anyone to create add-on repositories to share their add-ons for Home Assistant easily. This repository is providing HomA MQTT framework add-ons.

## Installation

Use the following URL to add this repository:

```txt
https://github.com/hass-hmueller01/homa-mqtt-addons
```

## Add-ons

This repository contains the following add-ons

### [MQTT Min/Max saver HomA add-on][min-max-saver-homa]

![Latest Version][min-max-saver-homa-version-shield]
![Supports aarch64 Architecture][aarch64-shield]
![Supports amd64 Architecture][amd64-shield]
![Supports armhf Architecture][armhf-shield]
![Supports armv7 Architecture][armv7-shield]
![Supports i386 Architecture][i386-shield]

### [OpenV vcontrold to HomA add-on][openv-homa]

![Latest Version][openv-homa-version-shield]
![Supports aarch64 Architecture][aarch64-shield]
![Supports amd64 Architecture][amd64-shield]
![Supports armhf Architecture][armhf-shield]
![Supports armv7 Architecture][armv7-shield]
![Supports i386 Architecture][i386-shield]

### [RESOL VBus to HomA add-on][resol-vbus-homa]

![Latest Version][resol-vbus-homa-version-shield]
![Supports aarch64 Architecture][aarch64-shield]
![Supports amd64 Architecture][amd64-shield]
![Supports armhf Architecture][armhf-shield]
![Supports armv7 Architecture][armv7-shield]
![Supports i386 Architecture][i386-shield]

### [SML to HomA add-on][sml-homa]

![Latest Version][sml-homa-version-shield]
![Supports aarch64 Architecture][aarch64-shield]
![Supports amd64 Architecture][amd64-shield]
![Supports armhf Architecture][armhf-shield]
![Supports armv7 Architecture][armv7-shield]
![Supports i386 Architecture][i386-shield]

<!--
Notes to developers after forking or using the github template feature:
- While developing comment out the 'image' key from 'example/config.yaml' to make the supervisor build the addon
  - Remember to put this back when pushing up your changes.
- When you merge to the 'main' branch of your repository a new build will be triggered.
  - Make sure you adjust the 'version' key in 'example/config.yaml' when you do that.
  - Make sure you update 'example/CHANGELOG.md' when you do that.
  - The first time this runs you might need to adjust the image configuration on github container registry to make it public
- Adjust the 'image' key in 'example/config.yaml' so it points to your username instead of 'home-assistant'.
  - This is where the build images will be published to.
- Rename the example directory.
  - The 'slug' key in 'example/config.yaml' should match the directory name.
- Adjust all keys/url's that points to 'home-assistant' to now point to your user/fork.
- Share your repository on the forums https://community.home-assistant.io/c/projects/9
- Do awesome stuff!
 -->

[min-max-saver-homa-version-shield]: https://img.shields.io/badge/version-v0.1.3-blue.svg
[min-max-saver-homa]: https://github.com/hass-hmueller01/addon-min-max-saver/tree/v0.1.3
[openv-homa-version-shield]: https://img.shields.io/badge/version-v0.1.8-blue.svg
[openv-homa]: https://github.com/hass-hmueller01/addon-openv-homa/tree/v0.1.8
[resol-vbus-homa-version-shield]: https://img.shields.io/badge/version-v0.1.5-blue.svg
[resol-vbus-homa]: https://github.com/hass-hmueller01/addon-resol-vbus-homa/tree/v0.1.5
[sml-homa-version-shield]: https://img.shields.io/badge/version-v0.1.4-blue.svg
[sml-homa]: https://github.com/hass-hmueller01/addon-sml-homa/tree/v0.1.4
[aarch64-shield]: https://img.shields.io/badge/aarch64-yes-green.svg
[amd64-shield]: https://img.shields.io/badge/amd64-yes-green.svg
[armhf-shield]: https://img.shields.io/badge/armhf-yes-green.svg
[armv7-shield]: https://img.shields.io/badge/armv7-yes-green.svg
[i386-shield]: https://img.shields.io/badge/i386-yes-green.svg
