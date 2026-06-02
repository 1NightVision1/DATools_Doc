# Operators

Tools at your hands.

## What are Blender operators?

In Blender, an operator is a script command that can be executed from menus, buttons, hotkeys, or the search bar. Operators can run wherever the current context allows, which makes them flexible and reusable.

## DATools operators

DATools ships with the following operators:

- `Floor It!`: move selected meshes so their lowest vertex rests on the floor plane at Z = 0.
- `Scale It!`: scale one selected object to match the active object's dimension on a chosen axis.
- `Mirror It!`: mirror selected mesh objects across the X, Y, or Z axis.
- `Shrink It!`: create decimated duplicates of selected meshes, with options to keep or replace originals.
- `Rez It!`: resize textures in selected objects' materials to a target resolution while preserving aspect ratio.
- `Map It!`: add or update texture coordinate and mapping nodes for selected mesh materials.
- `Import GLTF/GLB`, `Import FBX`, `Import STL`, and `Import USDZ`: import supported exchange formats through DATools I/O.
- `Export GLTF/GLB`, `Export FBX`, and `Export STL`: export selected or configured content through DATools I/O.

The add-on also exposes light helper controls in the `Light` panel. These use Blender's built-in light operators and active light properties rather than a custom DATools operator.

Custom script management is implemented through additional `dat.custom_script_*` operators in the add-on preferences. See `Custom Scripts` for the user workflow and script authoring contract.

Collision helper operators are currently WIP. They are documented in `I/O Tools`, but they are not considered usable yet.

## Using DATools operators

- Open the DAT panel in the 3D View sidebar: `View3D > Sidebar > DAT`.
- Select `Tools` for mesh operators or `Texture` for texture operators.
- Choose any operator and configure the options shown in the DATools panel or dialog.
- Each operator only runs when its expected selection and context requirements are met.

## Notes

- Operators in DATools are implemented as Blender `bpy.types.Operator` classes.
- DATools remembers the last-used options between runs where useful.
- You can access operators from Blender's search bar by typing their names, regardless of the current UI panel.
