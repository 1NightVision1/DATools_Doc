# Rez It!

The `dat.rez_it` operator resizes image textures used by selected mesh objects.

## What it does

Resizes copied image textures to a target resolution while preserving aspect ratio. The original materials and images remain available.

## How it works

- Works on selected objects of type `MESH`.
- Opens a dialog where the target texture resolution can be set.
- Copies each material used by selected objects and names the duplicate `Resize_{resolution}_{original_material_name}`.
- Assigns the copied material to the selected object's material slot.
- Walks each copied material's node tree and processes `TEX_IMAGE` nodes.
- Copies each image texture and names it `Resize_{resolution}_{original_texture_name}`.
- Resizes the copied image so its largest dimension equals the chosen resolution.
- Preserves aspect ratio by scaling the shorter dimension proportionally.
- Reuses already resized materials or images with matching names when possible.
- Stores the last texture resolution on the scene.

## Scene properties

- `context.scene.dat_textureresolution`: target texture resolution, default `1024`, minimum `1`.

## Usage

1. Select one or more mesh objects with image-textured materials.
2. Run `dat.rez_it` from the DATools `Texture` panel.
3. Set the target texture resolution in the dialog and confirm.

## Notes

- Only node-based materials with image texture nodes are resized.
- Packed images are unpacked before duplication when possible.
- The resized copies are assigned to the selected objects; originals are preserved with fake users where applicable.
