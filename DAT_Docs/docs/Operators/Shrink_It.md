# Shrink It!

The `dat.shrink_it` operator creates decimated duplicates of selected mesh objects and optionally replaces the originals.

## What it does

- Duplicates all selected mesh objects and their mesh data.
- Uses a Decimate modifier to reduce the duplicated object geometry according to a percentage.
- Can either keep the original meshes or replace them with the decimated duplicates.
- Optionally applies existing modifiers before decimation.
- Can automatically select the resulting objects after the operation.

## How it works

- Requires Object Mode and one or more selected mesh objects.
- Shows a dialog with the following options:
  - `Shrink Percentage`: how much geometry to keep (1–100).
  - `Shrink Mode`: `Keep Duplicates` or `Replace Originals`.
  - `Apply Modifiers`: whether to apply existing modifiers before decimation.
  - `Select Result`: whether to select the output objects after running.
- Duplicates each selected mesh and links the duplicate into the same collections.
- Adds a `DECIMATE` modifier to each duplicate, using `ratio = percentage / 100.0`.
- Applies the Decimate modifier and preserves the original selection state.
- If `Replace Originals` is selected, removes original objects and renames duplicates to the original names.
- Restores the previous selection and active object when possible.

## Scene Properties

- `context.scene.dat_shrinkpercentage`: last used shrink percentage.
- `context.scene.dat_shrink_mode`: `KEEP` or `REPLACE` mode.
- `context.scene.dat_shrink_apply_modifiers`: whether existing modifiers were applied before decimation.
- `context.scene.dat_shrink_select_result`: whether to select resulting objects after the operation.

## Usage

1. In Object Mode, select one or more mesh objects.
2. Run `dat.shrink_it` from the DAT panel.
3. Adjust the dialog properties and confirm.

## Notes

- If `Replace Originals` is selected, the original objects are removed and duplicates take their names.
- If the shrink percentage is outside 1–100, the operator cancels with a warning.
- The operator preserves existing scene settings so your last chosen values remain available.
