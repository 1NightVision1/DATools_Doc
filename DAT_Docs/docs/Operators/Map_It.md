# Map It!

The `dat.map_it` operator adds or updates texture mapping nodes on selected mesh materials.

## What it does

- Scans selected mesh objects for materials that use image texture nodes.
- Creates a Texture Coordinate node and a Mapping node when they are missing.
- Reuses existing DATools mapping nodes when they are already present.
- Connects the Mapping node output to each image texture node's `Vector` input.
- Lets you control texture mapping location, rotation, and scale on the X, Y, and Z axes.

## How it works

- Requires Object Mode and at least one selected mesh object.
- Enables node usage on each processed material.
- Finds all `TEX_IMAGE` nodes in each material node tree.
- Creates or reuses a `ShaderNodeTexCoord` node named `DAT_MapIt_TextureCoordinate`.
- Creates or reuses a `ShaderNodeMapping` node named `DAT_MapIt_Mapping` with the label `DAT Map It`.
- Links the Texture Coordinate `UV` output to the Mapping `Vector` input. If `UV` is unavailable, it falls back to `Generated`.
- Removes existing links to each image texture `Vector` input, then links the Mapping `Vector` output.
- Stores the last mapping values on scene properties.

## Live updates

After Map It! has created DATools mapping nodes, changing the mapping properties in the `Texture` panel updates selected materials that already contain a DATools mapping node. The panel also shows a live mapping count when selected materials can be updated this way.

## Scene properties

- `context.scene.dat_location_x`, `dat_location_y`, `dat_location_z`: mapping location offset.
- `context.scene.dat_rotation_x`, `dat_rotation_y`, `dat_rotation_z`: mapping rotation values.
- `context.scene.dat_scale_x`, `dat_scale_y`, `dat_scale_z`: mapping scale values.

## Usage

1. In Object Mode, select one or more mesh objects with materials that contain image texture nodes.
2. Open `View3D > Sidebar > DAT > Texture`.
3. Set the mapping location, rotation, and scale values.
4. Run `dat.map_it`.
5. Adjust the same values later to update selected materials that contain the DATools mapping node.

## Notes

- Materials without image texture nodes are skipped.
- The operator cancels with a warning if no image texture nodes are found on selected mesh materials.
- Existing non-DATools links to image texture `Vector` inputs are replaced by the DATools Mapping node connection.
