# Floor It!

The `dat.floor_it` operator works on selected mesh objects.

## What it does

Moves each selected mesh so its lowest world-space vertex is aligned with the floor at Z = 0.

## How it works

- Iterates over `context.selected_objects`.
- Skips objects that are not type `MESH` or have no vertices.
- Computes the minimum Z coordinate of all world-space vertices using `obj.matrix_world @ vert.co`.
- Subtracts that minimum from `obj.location.z`.
- Translates the mesh only along the Z axis, preserving X and Y placement.

## Usage

1. Select one or more mesh objects.
2. Run `dat.floor_it` from the DATools `Tools` panel.
3. The selected meshes move so their bottom-most geometry sits on Z = 0.

## Notes

- There are no extra options for this operator.
- The operator uses world-space vertex positions, so object transforms are included when finding the lowest point.
