# Mirror It!

The `dat.mirror_it` operator mirrors selected mesh objects across a chosen axis.

## What it does

- Mirrors all selected mesh objects using Blender's transform mirror operator.
- Uses the currently selected axis from the DAT panel or the last remembered scene value.
- Applies object scale after mirroring and recalculates normals for each mirrored mesh.

## How it works

- Requires one or more selected mesh objects in Object Mode.
- Reads `context.scene.dat_mirror` to determine the mirror axis: `X`, `Y`, or `Z`.
- Temporarily selects only mesh objects and sets the pivot point to `INDIVIDUAL_ORIGINS`.
- Calls `bpy.ops.transform.mirror` with the chosen constraint axis.
- Applies object scale with `bpy.ops.object.transform_apply(location=False, rotation=False, scale=True)`.
- Enters Edit Mode on each mirrored object to select all vertices and run `bpy.ops.mesh.normals_make_consistent()`.
- Restores the original selection, active object, and pivot point.

## Usage

1. In Object Mode, select one or more mesh objects.
2. Choose the mirror axis in the DAT panel.
3. Run `dat.mirror_it` from the DAT panel.

## Scene Properties

- `context.scene.dat_mirror`: stores the selected mirror axis.

## Notes

- The operator works only on selected objects of type `MESH`.
- It preserves the previous object selection and active object after completion.
- The selected mirror axis is remembered in the scene for subsequent operations.
