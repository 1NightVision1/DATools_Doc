# Scale It!

This operator works on mesh objects when exactly two objects are selected in Object Mode.

## What it does

Scales the non-active selected object so its dimension on one chosen axis matches the active object's dimension.

## How it works

- Requires Object Mode, exactly two selected objects, and a valid active object.
- Uses the active object as the source reference and the other selected object as the target.
- Reads `context.scene.dat_scale` to determine which axis to match: X, Y, or Z.
- Computes the source dimension from `active.dimensions[axis_index]` and the target dimension from `target.dimensions[axis_index]`.
- If the target dimension is zero, the operator cancels with an error.
- Calculates `scale_factor = source_dim / target_dim`.
- Temporarily selects only the target object, makes it active, and calls `bpy.ops.transform.resize(value=(scale_factor, scale_factor, scale_factor))`.
- Restores the original selection and active object after resizing.
- Stores the last scale factor and target object in scene properties.

## Variables

- `context.scene.dat_scale`: EnumProperty with values `X`, `Y`, `Z`; selects which axis dimension is matched.
- `context.scene.dat_scalebuffer`: FloatProperty that records the scale factor used.
- `context.scene.dat_activeobjectbuffer`: PointerProperty storing the target object after the operation.
- `active`: the active object used as the dimension source.
- `target`: the other selected object that is scaled.

## Usage

1. Select the object to scale first.
2. Select the reference object last so it becomes the active object.
3. Choose the axis in the DAT panel (`X`, `Y`, or `Z`).
4. Run `dat.scale_it`.

## Notes

- This operator applies a uniform scale to the target object based on the selected axis.
- The reference object remains unchanged.
