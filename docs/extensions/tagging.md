---
title: Tag downloaded files using Mutagen
---

Add episode and podcast titles to MP3/OGG tags.

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

This extension can optionally embed coverart - note that the coverart will not be
standardized in any way, so Rockbox users be wary. This is disabled by default.

This extension can optionally remove all tags instead of doing any of the above.
This is disabled by default.

## Dependencies

This extension requires python module `mutagen`.

| setting                                      | value      | description                                                                               | version           |
|----------------------------------------------|------------|-------------------------------------------------------------------------------------------|-------------------|
| extensions.tagging.strip\_album\_from\_title | **true**/false | true = removes the Album tag from the Title tag if the Title begins with the same string as the Album tag | all |
| extensions.tagging.genre\_tag                | Podcast    | Sets the Genre tag. Default = Podcast | all |
| extensions.tagging.always\_remove\_tags      | true/**false** | true = extension removes all tags instead of creating/adding tag information              | 3.5.0             |
| extensions.tagging.auto\_embed\_coverart     | true/**false** | true = embed channel cover art in file. | git master branch |
| extensions.tagging.set\_artist\_to\_album    | **True**/False | True = set the Artist tag to the same as the existing Album tag. | git master branch |
| extensions.tagging.set\_version              | 4              | Sets the id3 version which will be written | git master branch |
| extensions.tagging.modify\_tags              | **True**/False | Allow tags to be modified rather than simply added. If set to False, remove\_before\_modify has no effect | git master branch |
| extensions.tagging.remove\_before\_modify    | **True**/False | Delete all existing tags prior to writing new tags | git master branch |
| extensions.tagging.write\_title              | **True**/False | True = write the title field | git master branch |
| extensions.tagging.write\_album              | **True**/False | True = write the album field | git master branch |
| extensions.tagging.write\_subtitle           | True/**False** | True = write the subtitle field | git master branch |
| extensions.tagging.write\_comments           | True/**False** | True = write the comments field (with the subtitle) | git master branch |
| extensions.tagging.write\_genre              | **True**/False | True = write the genre with the genre\_tag setting | git master branch |
| extensions.tagging.write\_pubdate            | **True**/False | True = write the published date | git master branch |



Links:

-   [Extension Source](https://github.com/gpodder/gpodder/blob/master/share/gpodder/extensions/tagging.py)
