# Scale It!

The `dat.scale_it` operator scales one selected object to match the active object's dimension on a chosen axis.

## What it does

Scales the non-active selected object uniformly so its dimension on the selected axis matches the active object's dimension on that same axis.

## How it works

- Requires Object Mode, exactly two selected objects, and a valid active object.
- Uses the active object as the source reference.
- Uses the other selected object as the target to scale.
- Opens a dialog where the axis can be set to `X`, `Y`, or `Z`.
- Falls back to `context.scene.dat_scale` when run without the dialog.
- Computes `scale_factor = source_dimension / target_dimension`.
- Temporarily selects only the target object and calls `bpy.ops.transform.resize(value=(scale_factor, scale_factor, scale_factor))`.
- Restores the original selection and active object.
- Stores the last axis, scale factor, and target object on scene properties.

## Scene properties

- `context.scene.dat_scale`: selected axis, with values `X`, `Y`, or `Z`.
- `context.scene.dat_scalebuffer`: last scale factor used.
- `context.scene.dat_activeobjectbuffer`: target object from the last successful operation.

## Usage

1. Select the object to scale.
2. Select the reference object last so it becomes the active object.
3. Run `dat.scale_it` from the DATools `Tools` panel.
4. Choose the axis in the dialog and confirm.

## Notes

- The scale is uniform on all axes. The selected axis is only used to calculate the scale factor.
- The reference object remains unchanged.
- If the target object's selected-axis dimension is zero, the operator cancels.
