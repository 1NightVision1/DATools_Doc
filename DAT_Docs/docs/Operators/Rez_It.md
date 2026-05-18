# Rez It!

This operator works on selected mesh objects.

## What it does

Resizes image textures used by selected objects' materials to a target resolution while preserving aspect ratio.

## How it works

- Requires selected mesh objects in the scene.
- Reads the integer value from `context.scene.dat_textureresolution`.
- Copies each material used by selected objects and names the duplicate `Resize_{resolution}_{original_material_name}`.
- Walks each material's node tree and processes `TEX_IMAGE` nodes.
- Copies each image texture and names it `Resize_{resolution}_{original_texture_name}`.
- Resizes the copied image so its largest dimension equals the chosen resolution.
- Preserves aspect ratio by scaling the shorter dimension proportionally:
  - if width > height, height becomes `ceil(height * resolution / width)`
  - if width < height, width becomes `ceil(width * resolution / height)`
  - if width == height, both dimensions become `resolution`
- Assigns the new resized image to the material node.
- Reuses already resized textures or materials when possible to avoid duplicate processing.

## Variables

- `context.scene.dat_textureresolution`: IntProperty for the target texture resolution (`default=1024`, `min=1`).
- `processed_materials`: internal set to avoid recreating duplicate materials.
- `processed_textures`: internal set to avoid resizing the same texture multiple times.

## Usage

1. In Object Mode, select one or more mesh objects.
2. Set the desired texture resolution in the DAT panel.
3. Run `dat.rez_it`.

## Notes

- Only node-based materials with image texture nodes are resized.
- Packed images are unpacked before duplication when possible.
- The original textures and materials remain available; new copies are created for resized assets.
