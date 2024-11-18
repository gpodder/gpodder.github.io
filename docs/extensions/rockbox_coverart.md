---
title: Rockbox Cover Art Sync
---

This extension writes podcast subscription cover art to a media player.
This extension assumes that each podcast has its own folder on device.
Only folder-wide coverart is written - this extension does not do anything about
embedded cover art.

Cover art is converted to the desired file format and image size
via the python "pillow" module, and written to the desired filename.

Existing files (of the correct name) will be checked to see if they
need to be overwritten to conform to the size, baseline/progressive,
and file format parameters.

All jpegs will be written as "baseline" (rather than "progressive") type. Rockbox
only supports baseline jpegs.

## Dependencies

Requires python modules `pillow` and `filelock`. These are available on pip.

## Settings

| setting | value | description |
|---------|-------|-------------|
| extensions.rockbox_coverart.art_name_on_device  | cover.jpg | Desired filename on device. Only jpg, jpeg, and png filetypes allowed. |
| extensions.rockbox_coverart.convert_and_resize_art | **True**/False | Enable conversion and resize operations |
| extensions.rockbox_coverart.convert_size | 500 | Cover art will be resized to this size (square). If convert_allow_upscale_art=False, art smaller than this size will retain its size. Only used if convert_and_resize_art=True. |
| extensions.rockbox_coverart.convert_allow_upscale_art | True/**False** | Allow upscaling of art. If set to true, will allow images smaller than convert_size (square) to be upscaled to convert_size. Only used if convert_and_resize_art=True. |

Links:

- [Extension Source](https://github.com/gpodder/gpodder/blob/master/share/gpodder/extensions/rockbox_coverart.py)
