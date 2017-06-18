---
title: Tag downloaded files using Mutagen
---

Add episode and podcast titles to MP3/OGG tags

| setting                                      | value      | description                                                                               | version           |
|----------------------------------------------|------------|-------------------------------------------------------------------------------------------|-------------------|
| extensions.tagging.always\_remove\_tags      | true/false | true = extension removes all tags instead of creating/adding tag information              | 3.5.0             |
| extensions.tagging.auto\_embed\_coverart     | true/false | true = extension adds existing coverart after download                                    | git master branch |
| extensions.tagging.genre\_tag                | Genre      | with this setting you can define the genre tag. Default = Podcast                         | all               |
| extensions.tagging.strip\_album\_from\_title | true/false | true = removes the album name from the episode if the episode begins with the album title | all               |

Links:

-   [Extension Source](https://github.com/gpodder/gpodder/blob/master/share/gpodder/extensions/tagging.py)
-   [Flattr the Extension](https://flattr.com/thing/1203533/gPodder-Tagging-Extension)
