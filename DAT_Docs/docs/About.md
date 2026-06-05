# About

DAT Docs provides documentation for the DATools Blender add-on.

## What is DATools?

DATools is a Blender add-on designed to support the DungeonAlchemist import pipeline with utility tools for mesh, texture, and lighting preparation.

## Features

- `Floor It!` to snap meshes to the floor.
- `Scale It!` to match one object's dimension to another.
- `Mirror It!` to mirror selected meshes across an axis.
- `Shrink It!` to create decimated duplicates or replace originals.
- Asset tools to add bundled abstract reference assets or editable asset copies.
- `Rez It!` to resize image textures used by selected objects.
- `Map It!` to add or update texture coordinate and mapping nodes on selected materials.
- Light tools to add point, sun, spot, or area lights and edit the active light.
- A Script panel for running imported custom Python scripts inside DATools.
- I/O tools for GLTF/GLB, FBX, STL, and USDZ workflows.
- GLTF export profiles and export warnings for materials that may not be supported by Dungeon Alchemist.
- Collision helper settings for future use. These are currently WIP and not usable in production.
- Help buttons that open the relevant online documentation page from the DATools UI.
- A Help panel for opening documentation, reporting bugs, and requesting features.

## Where to find it

- The add-on appears in Blender's 3D View sidebar under the `DAT` tab.
- The panel is automatically available after enabling the add-on and contains `Blender`, `Tools`, `Asset`, `Texture`, `Light`, `Script`, `I/O`, `Settings`, and `Help` sections.
- DATools also adds import/export entries to Blender's top bar File menus.

## Language support

DATools includes a language selection mechanism that allows switching between English, Italian, German, and French from the add-on preferences.

## Current metadata

- Extension manifest version: `1.12.0`.
- Legacy `bl_info` version: `1.12.0`.
- Extension manifest minimum Blender version: `4.2.0`.
- Extension manifest maximum Blender version: `5.1.2`.
- Add-on location: `View3D > Sidebar > DAT`.
- Category: `3D View`.
- Maintainers: Tinazzi Patrick, Dallasrt.

## Permissions

- `files`: used for importing and exporting files.
- `network`: used only to open DATools online documentation and GitHub Issues from help buttons.

## Author

- Tinazzi Patrick
