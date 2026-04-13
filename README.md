# Custom Risco Integration for Home Assistant 2023.8.3

This repository contains a backported version of the official Home Assistant
**Risco** integration, based on the `2023.8.3` tag of the Home Assistant Core
repository.

## Note

This custom component is intended for users who remain on HA 2023.8.3
(32‑bit) and cannot upgrade to newer releases. It is not needed on
modern Home Assistant versions.

## Why this exists

Risco recently started blocking the default Home Assistant User-Agent string.
The upstream Python library **pyrisco** added a fix (custom User-Agent header)
in version `0.6.8`, but Home Assistant 2023.8.3 ships with an older pyrisco
version that no longer works.

This custom component allows Home Assistant 2023.8.3 users to continue using
their Risco alarm system by:

- overriding the built-in `risco` integration
- updating the dependency to `pyrisco==0.6.8`
- keeping all existing devices, entities, and automations intact

## Source

The integration code was copied from:
``https://github.com/home-assistant/core/tree/2023.8.3/homeassistant/components/risco``


Only minimal changes were made:

- added a `version` field to `manifest.json` (required for custom integrations)
- updated the `requirements` entry to use `pyrisco==0.6.8`

No functional changes were made to the integration itself.

## Installation

Copy the folder:

``custom_components/risco``


into your Home Assistant configuration directory:

``/config/custom_components/risco``


Restart Home Assistant.  
The custom integration will automatically override the built-in one.

## Notes

- Do **not** remove the built-in Risco integration from the UI.  
  Disable it instead to preserve all devices and entities.
- All existing entities will continue working because the domain and unique IDs
  remain unchanged.

## Changelog

### v1.0.0
- Initial release
- Backported Risco integration from HA 2023.8.3
- Updated pyrisco requirement to 0.6.8
- Added version field to manifest.json
