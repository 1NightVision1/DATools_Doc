# Light Tools

The `Light` panel provides quick access to Blender light creation and active light editing.

## What it does

- Adds common Blender light types from the DATools sidebar.
- Shows editable properties for the active light object.
- Keeps light controls near the mesh and texture preparation tools used by DATools.

## Add lights

The panel exposes buttons for Blender's built-in `object.light_add` operator:

- `Point`
- `Sun`
- `Spot`
- `Area`

Each button creates the matching Blender light type.

## Edit the active light

When the active object is a light, the panel shows the light data properties that are available for that light type:

- `type`
- `color`
- `energy`
- `shadow_soft_size`, when supported
- `angle`, when supported
- `size`, when supported
- `spot_size`, when supported
- `spot_blend`, when supported

If the active object is not a light, the panel displays a prompt to select a light before editing settings.

## Usage

1. Open `View3D > Sidebar > DAT > Light`.
2. Click `Point`, `Sun`, `Spot`, or `Area` to add a light.
3. Select a light object.
4. Adjust its available properties directly in the DATools Light panel.

## Notes

- These controls wrap Blender's built-in light creation and light data properties.
- No custom `dat.*` light operator is registered for these buttons.
