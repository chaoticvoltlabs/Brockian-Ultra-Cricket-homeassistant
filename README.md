# BUC Home Assistant

This repository contains the Home Assistant side of the current BUC + panel stack.

## Current role in the system

Home Assistant is the upstream system of record for:

- raw weather provider input
- derived panel weather entities
- indoor climate entities
- overview payload composition
- example scene and switch entities

The current chain is:

1. Home Assistant builds canonical entities and payloads.
2. BUC reads those entities and exposes compact panel APIs.
3. The panel consumes those APIs and sends control intents back through BUC.

## Related repositories

- [Brockian-Ultra-Cricket-server](https://github.com/chaoticvoltlabs/Brockian-Ultra-Cricket-server)
  - BUC server and compact API layer
- [Brockian-Ultra-Cricket-panel](https://github.com/chaoticvoltlabs/Brockian-Ultra-Cricket-panel)
  - embedded panel firmware client

## Current package ownership

- [`packages/panels/open_meteo_rest.yaml`](packages/panels/open_meteo_rest.yaml)
  - raw Open-Meteo REST source only
- [`packages/panels/open_meteo_current.yaml`](packages/panels/open_meteo_current.yaml)
  - canonical current-weather entities
- [`packages/panels/weather.yaml`](packages/panels/weather.yaml)
  - canonical forecast entities
- [`packages/panels/indoor.yaml`](packages/panels/indoor.yaml)
  - indoor room entities
- [`packages/panels/panel_payload.yaml`](packages/panels/panel_payload.yaml)
  - indoor payload composition
- [`packages/panels/overview.yaml`](packages/panels/overview.yaml)
  - overview payload composition

## Important canonical entities

- `sensor.panel_weather_current`
- `sensor.panel_weather_48h`
- `sensor.panel_weather_daily`
- `sensor.panel_indoor_payload`
- `sensor.panel_overview_payload`
- `input_boolean.panel_night_mode`

## Example scene assumptions

Scenes:

- `scene.room_work`
- `scene.room_evening`
- `scene.room_movie`
- `scene.room_night`

Direct controls:

- `light.room_light_a`
- `switch.room_light_b`
- `light.room_light_c`
- `switch.media_power`

## Documentation

- [`docs/architecture.md`](docs/architecture.md)
- [`docs/entities-and-payloads.md`](docs/entities-and-payloads.md)
- [`docs/scene-examples.md`](docs/scene-examples.md)
- [`docs/operations.md`](docs/operations.md)


## Copyright & license

PolyForm Noncommercial License 1.0.0
with Commercial Use by Explicit Permission Only
See LICENSE.txt


Copyright (c) 2026 Robin Kluit / Chaoticvolt.
