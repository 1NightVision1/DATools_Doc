# I/O Tools

The DATools `I/O` panel collects import and export actions for common Dungeon Alchemist pipeline formats.

## Where to find them

- Sidebar: `View3D > Sidebar > DAT > I/O`.
- Blender file menus:
  - `File > Import > DATools GLTF/GLB Import`
  - `File > Import > DATools FBX Import`
  - `File > Import > DATools STL Import`
  - `File > Import > DATools USDZ Import`
  - `File > Export > DATools GLTF/GLB Export...`
  - `File > Export > DATools FBX Export...`
  - `File > Export > DATools STL Export...`

## Import

DATools exposes quick import operators for:

- GLTF/GLB: `.gltf`, `.glb`
- FBX: `.fbx`
- STL: `.stl`
- USDZ: `.usdz`

Each import action opens Blender's file selector and then calls the compatible Blender importer for that format.

## Export

DATools exposes export operators for:

- GLTF/GLB
- FBX
- STL

FBX and STL exports are selection-based. They include a `Check Materials Before Export` option that can warn before exporting materials that may not be safe for the Dungeon Alchemist workflow.

## GLTF/GLB export

The GLTF/GLB exporter is the most configurable I/O workflow in DATools.

### Export options

- `Format`: choose `GLB (Binary)`, `GLTF + BIN + textures`, or `GLTF (Embedded)`.
- `Scope`: export the entire scene, visible objects, or only selected objects.
- `Apply Modifiers`: apply modifiers during export.
- `Materials`: export materials, use placeholder material slots, or export no materials.
- `Check Materials Before Export`: show a warning when unsupported material nodes are found.
- `Unicode`: keep UTF-8 text or strip accents for ASCII-safe JSON output.

### Geometry

- `Triangulate All`: temporarily triangulates exported mesh objects.
- `Curves to Mesh (temp)`: converts curves to temporary mesh objects for export.
- `Text to Mesh (temp)`: converts text objects to temporary mesh objects for export.
- `Surfaces to Mesh (temp)`: converts surfaces to temporary mesh objects for export.
- `Metaball to Mesh (temp)`: converts metaballs to temporary mesh objects for export.

Temporary conversion objects are removed after export.

### Object types

- `Include Empties`: includes empty objects.
- `Include Cameras`: includes cameras.
- `Lights`: excludes lights, exports only Sun lights, or exports all supported light types.
- `Exclude Unsupported Area Lights`: skips Area lights when enabled.

### Animations

- `Auto (if present)`: exports animations only when animation data is detected.
- `Export`: always exports animations.
- `Exclude`: never exports animations.

## Export profiles

GLTF export profiles store the exporter settings used by the dialog.

- The active profile is selected in the `I/O` panel or DATools preferences.
- Opening the GLTF/GLB exporter loads the active profile.
- Completing an export saves the current dialog options back to the active profile.
- `Save as New Profile` creates a new profile with the current export options.
- The built-in `Default` profile cannot be deleted.
- Non-default profiles can be deleted from the I/O panel or DATools preferences.

## Export warnings

When `Check Materials Before Export` is enabled, DATools checks exported materials for node types that may not be supported by Dungeon Alchemist.

Currently accepted node types include:

- Principled BSDF
- Image Texture
- Material Output
- Normal Map
- Texture Coordinate
- Reroute
- Mapping

If unsupported nodes are found, DATools shows an export warning with these actions:

- `Cancel`: stops the pending export.
- `Continue`: continues the export anyway.
- `Tag Warnings`: colors unsupported material nodes red so they are easier to find.
- `Open Console`: opens Blender's console for debugging.

## Collision helpers

**WIP: collision settings are still in development and are not usable yet.**

DATools currently shows collision helper controls in the I/O panel and GLTF exporter dialog so the workflow can be tested and documented early. Do not rely on these settings for production exports yet.

Visible collision controls include:

- `Toggle`: toggles the collision marker on selected objects.
- `Set On`: marks selected objects as collision objects.
- `Set Off`: removes the collision marker from selected objects.
- `Collision Prefix`: planned prefix-based collision naming, default `COL_`.
- `Use Prefix for Collisions`: planned GLTF export option.
- `Use Property for Collisions`: planned GLTF export option.
- `Write Collision Manifest (.json)`: planned sidecar manifest export.

The current collision marker key shown by DATools is `is_collision`.

Until this workflow is finished, treat collision helpers as non-functional WIP controls.
