# Scene Examples

## Purpose

The panel page-3 top row is scene-driven.

BUC expects explicit scene activation, not grouped toggle behavior.

## Example scenes

- `scene.room_work`
- `scene.room_evening`
- `scene.room_movie`
- `scene.room_night`

## How BUC uses them

Example mappings:

- `scene_work:activate` -> `scene.turn_on` `scene.room_work`
- `scene_evening:activate` -> `scene.turn_on` `scene.room_evening`
- `scene_movie:activate` -> `scene.turn_on` `scene.room_movie`
- `scene_night:activate` -> `scene.turn_on` `scene.room_night`

## Related direct controls

- `light.room_light_a`
- `switch.room_light_b`
- `light.room_light_c`
- `switch.media_power`

These direct controls are separate from the scene model and remain individual toggles.

## Naming rule

Use the Home Assistant scene entity IDs exactly as expected by BUC. Avoid informal variations or extra prefixes if BUC is already configured for the current names.
