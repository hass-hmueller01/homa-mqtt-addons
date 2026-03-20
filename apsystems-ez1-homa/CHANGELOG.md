<!-- https://developers.home-assistant.io/docs/add-ons/presentation#keeping-a-changelog -->
# Changelog

All changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/),
and this project adheres to [Semantic Versioning](https://semver.org/).

## [Unreleased]

## [1.0.0] - 2026-03-20
- Ported to Home Assistant add-on
- Updated to APsystemsEZ1 API 2.7.0
- Migrated from https://github.com/hmueller01/APsystems-EZ1-mqtt to https://github.com/hass-hmueller01/addon-apsystems-ez1-homa

## [0.5.0] - 2025-06-07
- Added support of daily energy info
- Inverter e1 output is energy generation after startup not per day

## [0.4.5] - 2025-06-02
- Fix power output (0W) if inverter is offline (no answer)

## [0.4.4] - 2025-05-22
- Fixed HASS device_class energy state_class warning

## [0.4.3] - 2025-05-04
- Updated to APsystemsEZ1 API 2.6.0
- Fixed exception at float conversion

## [0.4.2] - 2025-02-16
- Updated to APsystemsEZ1 API 2.5.0

## [0.4.1] - 2024-11-03
- Switch from `asyncio.gather()` to `async TaskGroup()`

## [0.4.0] - 2024-10-21
- Added APsystemsEZ1 2.4 API `enable_debounce=True`

## [0.3.0] - 2024-09-07
- Migrated to new APsystemsEZ1 2.x API

## [0.2.0] - 2024-07-25
- Fix timeout issues

## [0.1.0] - 2024-06-18
- Initial version
