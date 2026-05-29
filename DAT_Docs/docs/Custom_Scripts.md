# Custom Scripts

DATools can import custom Python scripts and display their UI inside the DATools `Script` panel.

## User workflow

1. Open `Edit > Preferences > Add-ons`.
2. Expand the DATools preferences.
3. In `Custom Scripts`, click the add button.
4. Select a `.py` file.
5. DATools copies the file into its managed `custom_scripts` folder and loads it.
6. Open `View3D > Sidebar > DAT > Script` to use active scripts.

## Script manager actions

Each imported script has controls for:

- Move up or down: changes display order in the Script panel.
- Active toggle: loads or unloads the script.
- Icon: changes the Blender icon identifier shown for the script.
- Show icon: controls whether the script icon appears in the Script panel.
- Show title: controls whether the script title appears in the Script panel.
- Rename: changes the display title.
- Replace source: imports a different `.py` file for that entry.
- Remove: unloads the script and removes DATools' managed copy.

## Supported script structure

Custom scripts are regular Python files loaded as temporary modules. DATools supports these optional entry points:

- `register()`: called when the script is loaded.
- `unregister()`: called when the script is unloaded.
- `classes`: a tuple or list of Blender classes to register if no `register()` function is provided.
- `draw(layout, context)`: called when DATools draws the script inside the Script panel.

If `draw(layout, context)` is missing, DATools shows a message asking the script to add one.

## Minimal example

```python
import bpy


class DAT_CUSTOM_OT_hello(bpy.types.Operator):
    bl_idname = "dat_custom.hello"
    bl_label = "Hello"

    def execute(self, context):
        self.report({"INFO"}, "Hello from a DATools custom script")
        return {"FINISHED"}


classes = (DAT_CUSTOM_OT_hello,)


def draw(layout, context):
    layout.operator("dat_custom.hello", icon="PLAY")
```

## Loading behavior

- Active scripts are loaded when DATools registers.
- Deactivating a script unloads its module and calls its unload path.
- Re-activating a script loads it again.
- If a script fails to load, DATools marks it inactive and reports the error.
- If a script UI fails while drawing, DATools shows the draw error inside the Script panel.

## Notes

- Only `.py` files can be imported.
- Script file names are sanitized before DATools creates its managed copy.
- Icon names must be valid Blender icon identifiers. Invalid icon values fall back to `FILE_SCRIPT` or are rejected when changed manually.
- Custom scripts run inside Blender, so they should follow normal Blender Python add-on safety rules.
