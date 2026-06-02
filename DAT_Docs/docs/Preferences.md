# Preferences

DATools preferences are available from Blender's add-on preferences after the add-on is enabled.

## Language

The language section shows the currently selected DATools language and provides buttons for:

- English
- Italian
- German
- French

Changing the DATools language stores the selected language in the add-on preferences. When Blender has the matching locale available, DATools also updates Blender's active interface language to that locale.

## Custom scripts

The preferences include a `Custom Scripts` manager. It is used to import Python scripts into DATools, activate or deactivate them, change their display title and icon, and control whether each script appears in the sidebar Script panel.

Imported scripts are copied into a `custom_scripts` folder inside the DATools add-on directory. Removing or replacing an imported script deletes DATools' internal copy when that copy is inside the managed folder. The original source file chosen during import is not removed by DATools.

## GLTF I/O

The preferences include a `GLTF I/O` section used by the I/O panel and GLTF exporter.

- `Collision Prefix`: WIP setting used by the unfinished collision workflow. The default value is `COL_`.
- `Active GLTF Profile`: selects the export profile loaded by the GLTF/GLB exporter dialog.
- `Delete Active`: removes the selected export profile when it is not the built-in `Default` profile.

The `Default` profile is built in and cannot be deleted. Export profiles store the options used by the GLTF/GLB exporter so repeated exports can start from the same settings.

Collision settings are still in development and are not ready for normal use.

## Icon Viewer preferences

DATools also shows an `Icon Viewer Preferences` box when Blender's Icon Viewer add-on is installed and enabled. This section exposes the Icon Viewer add-on's own preference fields, such as icon groups, popup behavior, and panel visibility.

If Icon Viewer is not enabled, DATools shows an informational message instead.
