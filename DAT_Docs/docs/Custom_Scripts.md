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

## Creating scripts with AI

You can ask an AI assistant to generate a DATools custom script for you. The safest results usually come from describing the exact action you want, the expected selection, and what should appear in the Script panel.

Ask for a single `.py` file that follows the DATools custom script contract:

- Include a `draw(layout, context)` function.
- Use Blender operators with unique `bl_idname` values, preferably under a custom prefix such as `dat_custom`.
- Put all Blender classes in a `classes = (...)` tuple.
- Use `bl_options = {"REGISTER", "UNDO"}` for operators that change the scene.
- Validate context before editing objects or data.
- Report clear messages with `self.report`.
- Avoid destructive file operations, background processes, network calls, and external Python dependencies.
- Avoid running scene-changing code at import time. Put actions inside operators.

### Base prompt

Copy this prompt and replace the bracketed parts with your request:

```text
Create a Blender Python script compatible with DATools Custom Scripts.

Goal:
[Describe exactly what the script should do.]

DATools compatibility requirements:
- Return one complete `.py` file only.
- The script must be importable by DATools without extra dependencies.
- Do not run scene-changing code at import time.
- Define one or more Blender operators for the actions.
- Use unique operator `bl_idname` values under the `dat_custom` prefix.
- Put all Blender classes in a `classes = (...)` tuple.
- Include a `draw(layout, context)` function that adds the UI controls for the DATools Script panel.
- Use `bl_options = {"REGISTER", "UNDO"}` for operators that modify the scene.
- Validate the current Blender context and selection before making changes.
- Use `self.report` for success, warning, and error messages.
- Return `{"FINISHED"}` on success and `{"CANCELLED"}` when requirements are not met.
- Do not use network access, subprocesses, background timers, or destructive file operations.
- Do not require packages that are not included with Blender.

User workflow:
[Describe what the user will select or configure before pressing the button.]

UI requirements:
[Describe button labels, toggles, sliders, or fields to show in draw(layout, context).]

Safety requirements:
[Describe anything that must be skipped, preserved, or confirmed.]

Output:
Provide only the Python code inside one code block.
```

### Review checklist

Before importing an AI-generated script into DATools, check that:

- It is a `.py` file.
- It imports in Blender without external packages.
- It has a `draw(layout, context)` function.
- It has unique operator names.
- It does not delete files, open network connections, or run actions immediately on import.
- It uses Undo for scene-changing actions.
- It handles empty selections or wrong object types gracefully.

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
