# Interface

DATools appears in Blender's 3D View sidebar under the `DAT` tab. The panel uses selectable sections so mesh, texture, lighting, and layout controls can stay in one place without crowding a single list of buttons.

## Panel sections

- `Blender`: reserved for Blender-related DATools controls.
- `Tools`: mesh operators, including Floor It!, Scale It!, Mirror It!, and Shrink It!.
- `Asset`: preview gallery for bundled abstract assets, with actions for adding references and editable copies.
- `Texture`: texture utilities, including Rez It! and Map It!.
- `Light`: controls for adding lights and editing the active light.
- `Script`: active custom scripts imported through DATools preferences.
- `I/O`: import/export tools for GLTF/GLB, FBX, STL, and USDZ, plus GLTF export profiles and WIP collision helpers.
- `Settings`: panel layout and display preferences.
- `Help`: quick links for documentation, bug reports, and feature requests.

## Selecting sections

- Click a section icon to show that section.
- Use Shift-click to show or hide multiple sections when `Shift Multiselect` is enabled.
- Use Ctrl-click on a section icon to pin or unpin it.
- Pinned sections stay visible when another section is selected.
- Use the disclosure control in each section header to collapse or expand it.

## Settings

The `Settings` panel exposes the layout preferences stored on the current scene:

- `Vertical Tabs`: places selector icons in a vertical toolbar.
- `Shift Multiselect`: uses Shift-click to add or remove visible panels.
- `Show Tab Labels`: displays text labels next to selector icons.
- `Menu Area Width`: controls how much width is used by the selector when tab labels are visible.
- `Menu Button Size`: scales the section selector buttons.
- `Menu Icon Size`: scales selector icons.
- `Submenu Button Size`: scales section header rows.
- `Text / Row Size`: scales text-bearing rows inside the panel.
- `Show Help Buttons`: shows question mark buttons that open the relevant documentation page.
- `Show Script Names`: shows custom script titles in the Script panel.
- `Show Script Icons`: shows custom script icons in the Script panel.
- `Align Script Buttons`: draws custom script controls in aligned rows.
- `Asset Gallery Size`: controls the preview popup scale for the Asset panel.

## Help buttons

When `Show Help Buttons` is enabled, DATools shows question mark buttons in supported tool headers. These buttons open the matching documentation page in Blender's browser URL operator.

Blender online access must be enabled for documentation buttons to open web pages.

## Help panel

The `Help` panel provides two quick support areas:

- `Bug Reports and Feature Requests`: opens the DATools GitHub Issues page.
- `Documentation`: opens the DATools online documentation home page.

When reporting an issue, include reproduction steps, the expected result, your Blender version, and your DATools version.

## Asset panel

The `Asset` panel displays bundled abstract assets from the DATools asset library. Select an asset thumbnail, then use the action buttons to add or toggle a reference, reimport it, add an editable copy, or remove all asset references.

## Script panel

The `Script` panel displays active custom scripts imported from the DATools add-on preferences. For each active script, DATools can show the configured title, icon, and any UI drawn by the script's `draw(layout, context)` function.

If no custom scripts are active, the panel displays an empty-state message.

## I/O panel

The `I/O` panel contains quick import and export actions:

- Import: GLTF/GLB, FBX, STL, and USDZ.
- Export: GLTF/GLB, FBX, and STL.
- Export Profile: select or delete the active GLTF export profile.
- Collision Helpers: WIP controls for future Dungeon Alchemist collision setup.

Collision helpers are currently visible for testing and documentation purposes, but they are still in development and should not be treated as production-ready.

## Language preferences

DATools language is selected from the add-on preferences. The available languages are English, Italian, German, and French. Selecting a language also updates Blender's active interface language to the matching locale when available.
