# Home Assistant Architecture

## Purpose

This repository contains the Home Assistant package/config layer that feeds BUC and receives the effects of BUC-translated control actions.

## System position

Home Assistant currently owns:

- raw integrations and provider data
- derived weather entities for the panel/BUC pipeline
- indoor climate entities
- payload composition
- switch and scene entities used by the panel control path

## Weather ownership model

### Raw provider

- [`packages/panels/open_meteo_rest.yaml`](../packages/panels/open_meteo_rest.yaml)

Owns:

- `sensor.open_meteo_raw_weather`

This file should contain raw provider input only.

### Current weather

- [`packages/panels/open_meteo_current.yaml`](../packages/panels/open_meteo_current.yaml)

Owns:

- `sensor.panel_weather_current`
- current-weather derivative helper sensors

### Forecast

- [`packages/panels/weather.yaml`](../packages/panels/weather.yaml)

Owns:

- `sensor.panel_weather_48h`
- `sensor.panel_weather_daily`

## Payload ownership model

### Indoor

- [`packages/panels/indoor.yaml`](../packages/panels/indoor.yaml)
  - canonical room temperature/humidity entities

- [`packages/panels/panel_payload.yaml`](../packages/panels/panel_payload.yaml)
  - `sensor.panel_indoor_payload`

### Overview

- [`packages/panels/overview.yaml`](../packages/panels/overview.yaml)
  - `sensor.panel_overview_payload`
  - `input_boolean.panel_night_mode`

Overview should compose from canonical derived sensors, not duplicate weather derivation logic.

## Downstream consumers

### BUC reads

- `sensor.panel_weather_current`
- `sensor.panel_weather_48h`
- `sensor.panel_weather_daily`
- `sensor.panel_indoor_payload`
- `sensor.panel_overview_payload`
- `input_boolean.panel_night_mode`

### Panel control path affects

- example scene entities
- example direct-control entities
