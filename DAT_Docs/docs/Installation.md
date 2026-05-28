# Installation

Follow these steps to install the DATools add-on and use the documentation site.

## Prerequisites

- Blender 4.2 or later when installing from the Blender extension manifest.
- A copy of the DATools add-on folder.
- Basic familiarity with installing Blender add-ons.

## Install DATools in Blender

1. Open Blender.
2. Go to `Edit > Preferences > Add-ons`.
3. Click `Install...` and locate the DATools add-on ZIP file or folder.
4. Enable the `DATools` add-on by checking its checkbox.
5. Confirm the add-on appears in the `3D View` sidebar under the `DAT` tab.

The extension manifest declares `blender_version_min = "4.2.0"`. The legacy `bl_info` metadata currently lists Blender 5.1, so if you install the add-on through a legacy add-on flow, Blender may display that value in the add-on information.

## Using the DATools UI

- The add-on is located in the 3D Viewport sidebar: `View3D > Sidebar > DAT`.
- Use `Tools` for mesh operators: Floor It!, Scale It!, Mirror It!, and Shrink It!.
- Use `Texture` for texture operators: Rez It! and Map It!.
- Use `Light` to add common light types or edit the active light.
- Use `Settings` to adjust the DATools panel layout, tab labels, button scale, icon scale, and row scale.

## Language Support

DATools supports multiple languages through the add-on preferences:

1. Open `Edit > Preferences > Add-ons`.
2. Find `DATools` and expand its preferences.
3. Select a language using the provided buttons.

## Documentation Site

- The documentation source lives in the `DAT_Docs/docs` folder.
- Use MkDocs to build or serve the site if desired.
- The generated site files are available under `DAT_Docs/site`.
