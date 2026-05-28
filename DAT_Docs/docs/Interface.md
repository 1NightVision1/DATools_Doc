# Interface

DATools appears in Blender's 3D View sidebar under the `DAT` tab. The panel uses selectable sections so mesh, texture, lighting, and layout controls can stay in one place without crowding a single list of buttons.

## Panel sections

- `Blender`: reserved for Blender-related DATools controls.
- `Tools`: mesh operators, including Floor It!, Scale It!, Mirror It!, and Shrink It!.
- `Texture`: texture utilities, including Rez It! and Map It!.
- `Light`: controls for adding lights and editing the active light.
- `I/O`: reserved for import and export tools.
- `Settings`: panel layout and display preferences.

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

## Language preferences

DATools language is selected from the add-on preferences. The available languages are English, Italian, German, and French. Selecting a language also updates Blender's active interface language to the matching locale when available.
