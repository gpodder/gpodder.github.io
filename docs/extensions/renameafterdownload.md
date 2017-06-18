---
title: Rename episode after the download
---

Rename episodes to "<Episode Title>.<ext>" on download

Configuration options ([in Git as of 2015-09-29](https://github.com/gpodder/gpodder/commit/bf31b911b6e9717ea3c7d42a36fd71f8899c193a)):

-   `add_sortdate` - If enabled, will add the sortdate of the episode (YYYY-MM-DD) at the front of the filename
-   `add_podcast_title` - If enabled, will add the podcast title at the front of the filename

If both `add_sortdate` and `add_podcast_title` are enabled, the sortdate will come before the episode (e.g. "`2015-09-29` `-` `Podcast` `Name` `-` `Episode` `Name.ext`").

Links:

-   [Extension Source](https://github.com/gpodder/gpodder/blob/master/share/gpodder/extensions/rename_download.py)
-   [Flattr the Extension](https://flattr.com/thing/1248762/gPodder-Video-Converter-Extension)
