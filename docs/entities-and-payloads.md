# Entities And Payloads

## Canonical entities used by BUC

### Weather

- `sensor.panel_weather_current`
- `sensor.panel_weather_48h`
- `sensor.panel_weather_daily`

### Payloads

- `sensor.panel_indoor_payload`
- `sensor.panel_overview_payload`
- `input_boolean.panel_night_mode`

## Canonical ownership

- raw Open-Meteo source:
  - `packages/panels/open_meteo_rest.yaml`
- current weather:
  - `packages/panels/open_meteo_current.yaml`
- 48h and daily forecast:
  - `packages/panels/weather.yaml`
- indoor payload:
  - `packages/panels/panel_payload.yaml`
- overview payload:
  - `packages/panels/overview.yaml`

## Current contract expectations

### `sensor.panel_weather_current`

Used by BUC as the current weather source for `/api/panel/weather`.

Expected fields include:

- `t`
- `feels_like`
- `rh`
- `pressure`
- `ws`
- `ws_bft`
- `wg`
- `wg_bft`
- `wd`
- `precip`

### `sensor.panel_weather_48h`

Expected to expose a `forecast` attribute containing compact hourly wind-oriented entries.

### `sensor.panel_weather_daily`

Expected to expose a `days` attribute containing compact daily forecast entries.

### `sensor.panel_indoor_payload`

Expected to expose `tiles` for the indoor page.

### `sensor.panel_overview_payload`

Expected to expose overview-oriented weather and pressure-trend data used by BUC enrichment.

It also carries a top-level `night_mode` boolean so downstream renderers can switch palette or theme without inventing a separate local schedule.
