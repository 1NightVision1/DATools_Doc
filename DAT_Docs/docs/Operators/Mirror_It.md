# Mirror It!

The `dat.mirror_it` operator mirrors selected mesh objects across a chosen axis.

## What it does

- Mirrors all selected mesh objects using Blender's transform mirror operator.
- Lets you choose the mirror axis from a dialog or the last stored scene value.
- Applies object scale after mirroring.
- Recalculates normals for each mirrored mesh.

## How it works

- Works on selected objects of type `MESH`.
- Opens a dialog where the axis can be set to `X`, `Y`, or `Z`.
- Temporarily selects only mesh objects.
- Sets the transform pivot point to `INDIVIDUAL_ORIGINS`.
- Calls `bpy.ops.transform.mirror` with the chosen constraint axis.
- Applies object scale with `bpy.ops.object.transform_apply(location=False, rotation=False, scale=True)`.
- Enters Edit Mode for each mirrored object, selects all vertices, and runs `bpy.ops.mesh.normals_make_consistent()`.
- Restores the original selection, active object, and pivot point.

## Remembered values

- Mirror axis: `X`, `Y`, or `Z`.

## Usage

1. In Object Mode, select one or more mesh objects.
2. Run `dat.mirror_it` from the DATools `Tools` panel.
3. Choose the mirror axis in the dialog and confirm.

## Notes

- The selected mirror axis is remembered in the scene for subsequent operations.
- Non-mesh selected objects are ignored.
