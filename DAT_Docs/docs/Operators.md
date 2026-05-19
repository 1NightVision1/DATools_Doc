# Operators
Tools at your hands.

## What are Blender operators?
In Blender, an operator is a script command that can be executed from menus, buttons, hotkeys, or the search bar. Operators can run wherever the current context allows, which makes them flexible and reusable.

## DATools operators
DATools ships with the following operators:

- `Floor It!` – move selected meshes so their lowest vertex rests on the floor plane at Z = 0.
- `Scale It!` – scale one selected object to match the active object's dimension on a chosen axis.
- `Mirror It!` – mirror selected mesh objects across the X, Y, or Z axis.
- `Shrink It!` – create decimated duplicates of selected meshes, with options to keep or replace originals.
- `Rez It!` – resize textures in selected objects' materials to a target resolution while preserving aspect ratio.

## Using DATools operators

- Open the DAT panel in the 3D View sidebar: `View3D > Sidebar > DAT`.
- Select the `Tools` menu in the panel to display operator buttons.
- Choose any operator and configure the available scene properties as needed.
- Each operator only runs when its expected selection and context requirements are met.

## Notes

- Operators in DATools are implemented as Blender `bpy.types.Operator` classes.
- Scene properties are used to store operator settings between runs.
- You can access operators from Blender's search bar by typing their names, regardless of the current UI panel.