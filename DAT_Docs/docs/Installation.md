# Installation

Follow these steps to install the DATools add-on and use the documentation site.

## Prerequisites

- Blender 4.2 or later when installing from the Blender extension manifest.
- An internet connection when installing from the DATools repository.
- A copy of the DATools add-on ZIP file or folder when installing manually.
- Basic familiarity with installing Blender add-ons.

## Install DATools in Blender

### Method 1: install from the Blender repository (recommended)

Installing DATools from the Blender repository is the recommended method because Blender can find the extension from the remote repository and check for available updates.

1. Open Blender.
2. Go to `Edit > Preferences > Get Extensions`.
3. Open the repositories settings and click the `+` button.
4. Choose `Add Remote Repository`.
5. Paste this repository URL:

   ```text
   https://nightvision-tools.github.io/DATools/index.json
   ```

6. Confirm the repository and refresh the remote extensions list if needed.
7. Search for `DATools`, then click `Install`.
8. Enable DATools if Blender does not enable it automatically.
9. Confirm the add-on appears in the `3D View` sidebar under the `DAT` tab.

<video controls width="100%">
  <source src="../assets/videos/install-blender-repo.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>

For more details about Blender extension repositories, see the [official Blender Extensions preferences documentation](https://docs.blender.org/manual/en/latest/editors/preferences/extensions.html).

### Method 2: install from a ZIP file or folder

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
