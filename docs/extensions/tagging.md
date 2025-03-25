---
title: Tag downloaded files using Mutagen
---

Add tags to MP3/MP4/OGG files after download.

By default, this extension will:
   - Remove existing tags
   - Write the Title tag, stripping the album from the beginning of the Title if necessary
   - Write the Album tag
   - Write the Artist tag (with the same string as the Album tag)
   - Write the Genre (to "Podcast", configurable)
   - Write the publish date

Also available are writing the Subtitle tag and the Comments tag (both with the
subtitle field), but the subtitle is often so long that it may cause problems with
certain audio players, such as Rockbox players. These are disabled by default.

This extension can optionally embed coverart - art can either be the channel artwork
or episode-specific artwork already embedded in the file. By default, the episode
artwork will be preferred if it is present - if not, the channel artwork will be used.

Note that episode-specific artwork in MP4 files is currently not implemented.

The artwork can optionally be normalized to the desired parameters - size and file type.
By default, it will write 500px baseline JPEGs.

This extension can optionally remove all tags instead of doing any of the above.
This is disabled by default.

## Dependencies

This extension requires python modules `mutagen` and `pillow`.

| setting                                      | value      | description                                                                               | version           |
|----------------------------------------------|------------|-------------------------------------------------------------------------------------------|-------------------|
| extensions.tagging.strip\_album\_from\_title | **true**/false | Remove the Album tag from the Title tag if the Title begins with the same string as the Album tag | all |
| extensions.tagging.genre\_tag                | Podcast    | Value for the Genre tag | all |
| extensions.tagging.always\_remove\_tags      | true/**false** | Remove all tags instead of creating/adding tag information              | 3.5.0 and newer             |
| extensions.tagging.set\_artist\_to\_album    | **True**/False | Set the Artist tag to the same as the existing Album tag | git master branch |
| extensions.tagging.set\_version              | 4              | Sets the id3 version which will be written | git master branch |
| extensions.tagging.modify\_tags              | **True**/False | Allow tags to be modified rather than simply added. If set to False, remove\_before\_modify has no effect | git master branch |
| extensions.tagging.remove\_before\_modify    | **True**/False | Delete all existing tags prior to writing new tags | git master branch |
| extensions.tagging.auto\_embed\_coverart           | true/**false** | Embed cover art in file | git master branch |
| extensions.tagging.prefer\_channel\_coverart | true/**false** | Prefer embedding the channel coverart if available over the episode coverart | git master branch |
| extensions.tagging.normalize\_coverart       | **true**/false | Normalize the coverart to the desired size and file type before embedding it | git master branch |
| extensions.tagging.episode\_coverart\_size   | 500            | Desired size (in pixels) of coverart. Only used if normalize\_coverart is True | git master branch |
| extensions.tagging.episode\_coverart\_filetype | 0 (JPEG)     | Desired filetype of coverart. integer value, maps to 0=JPEG, 1=PNG. Only used if normalize\_coverart is True | git master branch |
| extensions.tagging.write\_title              | **True**/False | Write the title field | git master branch |
| extensions.tagging.write\_album              | **True**/False | Write the album field | git master branch |
| extensions.tagging.write\_subtitle           | True/**False** | Write the subtitle field | git master branch |
| extensions.tagging.write\_comments           | True/**False** | Write the comments field (with the subtitle) | git master branch |
| extensions.tagging.write\_genre              | **True**/False | Write the genre with the genre\_tag setting | git master branch |
| extensions.tagging.write\_pubdate            | **True**/False | Write the published date | git master branch |



Links:

-   [Extension Source](https://github.com/gpodder/gpodder/blob/master/share/gpodder/extensions/tagging.py)
