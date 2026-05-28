# Shrink It!

The `dat.shrink_it` operator creates decimated duplicates of selected mesh objects and can optionally replace the originals.

## What it does

- Duplicates all selected mesh objects and their mesh data.
- Adds and applies a Decimate modifier to each duplicate.
- Keeps the original meshes by default.
- Can replace original objects with the decimated duplicates.
- Can apply existing modifiers on duplicates before decimation.

## How it works

- Requires Object Mode and one or more selected mesh objects.
- Opens a dialog with shrink settings.
- Duplicates each selected mesh and links the duplicate to the same collections as the source object.
- Names duplicates with the `_Shrink` suffix before any optional replacement rename.
- Adds a `DECIMATE` modifier using `ratio = shrink_percentage / 100.0`.
- Applies the Decimate modifier.
- In `REPLACE` mode, removes original objects and renames duplicates to the original names.
- Restores selection and active object when possible.

## Dialog options

- `Shrink Percentage`: percentage of geometry to keep, from 1 to 100.
- `Shrink Mode`: `Keep Duplicates` or `Replace Originals`.
- `Apply Modifiers`: applies existing modifiers on duplicates before decimation.
- `Select Result`: selects replacement results when originals are no longer present.

## Scene properties

- `context.scene.dat_shrinkpercentage`: last used shrink percentage.
- `context.scene.dat_shrink_mode`: `KEEP` or `REPLACE`.
- `context.scene.dat_shrink_apply_modifiers`: whether existing modifiers are applied before decimation.
- `context.scene.dat_shrink_select_result`: whether replacement results should be selected after the operation.

## Usage

1. In Object Mode, select one or more mesh objects.
2. Run `dat.shrink_it` from the DATools `Tools` panel.
3. Adjust the dialog properties and confirm.

## Notes

- If `Keep Duplicates` is selected, the original objects remain in the scene and the duplicates are added beside them.
- If `Replace Originals` is selected, the original objects are removed and duplicates take their names.
- If the shrink percentage is outside 1 to 100, the operator cancels with a warning.
