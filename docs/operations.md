# Operations

## Current config loading model

Top-level config:

- [`configuration.yaml`](../configuration.yaml)

Packages:

- `homeassistant: packages: !include_dir_named packages`

Panel-related packages currently live under:

- [`packages/panels`](../packages/panels)

## Common follow-up actions after changes

After package changes, perform the appropriate Home Assistant reload or restart so updated template/rest/package definitions are applied.

Typical checks:

1. verify template entities exist
2. verify panel weather entities are unique and not duplicated
3. verify scenes exist with the expected entity IDs
4. verify BUC can read the expected sensors

## Current important assumptions

- `sensor.panel_weather_current` exists and is valid
- `sensor.panel_weather_48h` exists and is valid
- `sensor.panel_weather_daily` exists and is valid
- `sensor.panel_indoor_payload` exists and is valid
- `sensor.panel_overview_payload` exists and is valid
- `input_boolean.panel_night_mode` exists if you want panel-wide day/night switching
- example scene IDs match the BUC command mappings

## Repo notes

This repository is intentionally separate from `BUC` and `panel` because it is its own system layer with its own release/deploy cadence.
