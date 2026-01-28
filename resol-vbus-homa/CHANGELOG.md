<!-- https://developers.home-assistant.io/docs/add-ons/presentation#keeping-a-changelog -->
# Changelog

All changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/),
and this project adheres to [Semantic Versioning](https://semver.org/).

## [Unreleased]
### Changed
- Replaced deprecated object_id by default_entity_id in homeassistant_config
- Set LOG_TIMESTAMP to %Y-%m-%d %T

## [1.0.0] - 2025-12-08
- Removed armhf, armv7, i386 architectures as removed in home-assistant/builder 2025.11.0

## [0.1.8] - 2025-11-08
### Updated
- resol-vbus-python

## [0.1.7] - 2025-10-16
- Using template for "Umschaltventil Position" (0 = Heizung, 100 = Kessel)

## [0.1.6] - 2025-10-04
- Added icon

## [0.1.5] - 2025-10-02
- Changed from spec_file to RESOL device_name

## [0.1.4] - 2025-10-02
- Initial git version

## [0.1.0] - 2025-09-21
- Initial release
