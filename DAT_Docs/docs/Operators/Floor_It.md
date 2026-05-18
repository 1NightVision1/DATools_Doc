# Floor It!

This operator works on selected mesh objects.

## What it does

Moves each selected mesh so its lowest world-space vertex is aligned with the floor at Z = 0.

## How it works

- Iterates over `context.selected_objects`.
- Skips objects that are not type `MESH` or have no vertices.
- Computes the minimum Z coordinate of all world-space vertices using `obj.matrix_world @ vert.co`.
- Subtracts that minimum from `obj.location.z`.
- The mesh is translated only along the Z axis, preserving X/Y placement.

## Usage

1. In Object Mode, select one or more mesh objects.
2. Run the `dat.floor_it` operator from the DAT panel.
3. The meshes will be shifted so their bottom-most geometry sits on Z = 0.

## Notes

- There are no extra options for this operator.
- It uses the selected objects and their world transform to determine the lowest point.
