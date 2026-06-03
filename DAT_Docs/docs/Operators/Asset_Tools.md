# Asset Tools

The DATools `Asset` panel provides a thumbnail gallery for bundled abstract assets used as layout or reference helpers.

## What it does

- Reads assets from the bundled `DA_Abstract_Asset.blend` library.
- Shows available assets as thumbnail previews.
- Adds the selected asset as a scene reference.
- Toggles existing reference assets between visible and hidden.
- Reimports a selected reference asset from the bundled library.
- Adds editable copies that are separate from the original reference object.
- Removes all reference assets while leaving editable copies untouched.

## Where to find it

Open `View3D > Sidebar > DAT > Asset`.

## Asset gallery

The asset gallery is populated from the bundled asset library:

- Asset library: `asset/DA_Abstract_Asset.blend`
- Thumbnails: `asset/thumbs`

If the asset library is missing, unreadable, or empty, DATools shows an error or empty-state message in the Asset panel.

## Actions

Select an asset thumbnail first, then use the action buttons:

- `Add / Hide Asset`: adds the selected asset if it is not already present. If the reference already exists, the same button toggles its viewport and render visibility.
- `Reimport Asset`: removes the current reference object and imports a fresh copy from the bundled library.
- `Add Copy Asset`: appends the selected asset as a renamed editable copy. The copy uses its own object name and duplicated mesh data.
- `Remove All Assets`: removes all bundled reference assets from the scene. Renamed editable copies are left in place.

## Reference assets and editable copies

Reference assets keep their original bundled asset names. DATools uses those names to decide whether an asset is already present and can be hidden, shown, reimported, or removed.

Editable copies are renamed with a `_Copy` suffix and are intended for changes. Because they are no longer named like the original bundled references, `Remove All Assets` leaves them untouched.

## Settings

The `Settings` panel includes `Asset Gallery Size`, which controls the size of the asset preview popup.

## Notes

- The Asset panel depends on the bundled `.blend` library being present in the DATools add-on folder.
- Adding or reimporting an asset selects the imported object.
- Removing all assets asks for confirmation before deleting reference objects.
