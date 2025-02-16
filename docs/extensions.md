---
title: Extensions
---

Extensions are gPodder's mechanism for adding optional features and allowing easy customizability. Some extensions are already activated by default if you are running a specific environment (e.g. Ubuntu Unity support in gPodder 3 is implemented as an extension).

Sometimes the ordering of extensions is important. gPodder parses the filenames of extensions for a prefix, like "50_". When it finds a prefix like this, it sorts according to said prefix, with lower numbers higher. *Note that this does not use "natural sorting", so "100" comes between "10" and "11".* Extensions found without a prefix will be given the lowest two-digit priority, "99". If multiple instances of an extension are desired, the base name must be different, not just the prefix.

Extensions found within the user extension directory with the same base name (regardless of whether the prefix matches, or is present at all) override extensions provided with gPodder in the system directory.

### Default Extensions Included With gPodder

The following extensions are included with gPodder 3:

-   [**Audio Converter**] - Transcode audio files to mp3/ogg
-   **Convert video files to MP4 for Rockbox** - Converts all videos to a Rockbox-compatible format
-   [**Enqueue in media players**] - Add a context menu item for enqueueing episodes in installed media players
-   [**Filter episodes**] - to prevent automatic download of episodes matching a pattern, useful for mixed feeds
-   **Gtk Status Icon** - Show a status icon for Gtk-based Desktops
-   **Gtk+ Desktop Notifications** - Display notification bubbles for different events.
-   **Minimize on start** - Minimizes the gPodder window on startup.
-   [**MPRIS Listener**] - listen to notifications from MPRIS-capable players and translate them to gPodder's [Media Player D-Bus API]
-   [**Normalize audio with re-encoding**] - Normalize the volume of audio files with normalize-audio
-   **Notification Bubbles for Windows** - 'Display notification bubbles for different events.
-   [**Remove cover art from OGG files**] - removes coverart from all downloaded ogg files
-   [**Rename episodes after download**] - Rename episodes to “<Episode Title>.<ext>” on download
-   [**Search for new episodes on startup**] - Starts the search for new episodes on startup
-   **Sonos** - Stream podcasts to Sonos speakers
-   **Subtitle Downloader for TED Talks** - Downloads .srt subtitles for TED Talks Videos
-   [**Tag downloaded files using Mutagen**] - Add episode and podcast titles to MP3/OGG tags
-   **Taskbar Progress** - Displays the progress on the Windows taskbar
-   **Ubuntu App Indicator** - Show a status indicator in the top bar.
-   **Ubuntu Unity Integration** - Show download progress in the Unity Launcher icon.
-   [**Video Converter**] - Transcode video files to avi/mp4/m4v
-   [**Youtube_dl**] - enhanced youtube subscriptions and downloads using youtube-dl


### How To Write Your Own Extension

Extensions are a great way to customize your gPodder workflow: you'll be able to customize the UI, rename, modify or trigger
external programs when episodes are downloaded, etc..


#### Getting started

1. Extensions are loaded from the `Extensions` folder in the [gPodder Home Folder](#default-gpodder-home-folder).
The folder doesn't exist by default, so create it.

2. An example extension is available [here](https://github.com/gpodder/gpodder/blob/master/share/gpodder/examples/hello_world.py).
   Copy it to **GPODDER\_HOME/Extensions** and restart gPodder.

3. Extensions are activated from the **Extensions** pane of the **Preferences** dialog.
   Activate the **Hello World Extension** to get a item in the **Extras** menu called
   **Say Hello**.

4. Modify the `Message`, restart gPodder and see the updated notification when you click **Say Hello**.


#### Doing something useful

Maybe an existing extension does something similar to what you want
([rename after download](https://github.com/gpodder/gpodder/blob/master/share/gpodder/extensions/rename_download.py),
[tagging](https://github.com/gpodder/gpodder/blob/master/share/gpodder/extensions/tagging.py),
[run a command after download](https://github.com/gpodder/gpodder/blob/master/share/gpodder/extensions/command_on_download.py), ...).
Find inspiration in [its source code](https://github.com/gpodder/gpodder/tree/master/share/gpodder/extensions).

To see how an extension is loaded and every available callback, take a look at [extensions.py](https://github.com/gpodder/gpodder/blob/master/src/gpodder/extensions.py);
every method annotated with `@call_extensions` can be overriden in your extension. Check its parameters and return type.

gPodder's [model](https://github.com/gpodder/gpodder/blob/master/src/gpodder/model.py#L197) is quite straightforward.
Given an episode `e`:
 - get its title via `e.title`, its url via `e.url`
 - get the channel's subscription url via `e.channel.url`.


#### Debugging your extension

If your extension doesn't appear in the list,
be sure:
  - that its `__only_for__` or `__disable_in__` instructions (if any) apply to your system.
  - to run gpodder in debug mode (`gpodder -v`, [Windows](https://gpodder.github.io/docs/windows.html#debugging-gpodder-on-windows))
  and check that it's found and there isn't any error message:
```
[gpodder.extensions] DEBUG: Found extension "hello_world" in .../Extensions/hello_world.py
[gpodder.extensions] INFO: Module loaded: .../Extensions/hello_world.py

```

You should run `gpodder -v` anyway, because any log with lower priority than `logger.warn` is suppressed by default.

Feel free to ask for advice in the [mailing list](mailing-list) or as github issues:
we are always pleased to see you customize gPodder to your own needs.

Also, you may have to modify code in gPodder itself to achieve a particular goal.
This is OK: no need to recompile anything: just edit the **.py** and restart...


[**Audio Converter**]: extensions/audioconverter.md
[**Enqueue in media players**]: extensions/enqueueinmediaplayer.md
[**Filter Episodes**]: extensions/filter.md
[**Normalize audio with re-encoding**]: extensions/normalizeaudio.md
[**Rename episodes after download**]: extensions/renameafterdownload.md
[**Remove cover art from OGG files**]: extensions/removeoggcover.md
[**Tag downloaded files using Mutagen**]: extensions/tagging.md
[**Search for new episodes on startup**]: extensions/searchepisodeonstartup.md
[**Video Converter**]: extensions/videoconverter.md
[**MPRIS Listener**]: extensions/mprislistener.md
[**Youtube_dl**]: extensions/youtubedl.md
[Media Player D-Bus API]: https://github.com/gpodder/gpodder/commit/ab48ea24f29a3d237396848520d27b3dba23635d
[hello world extension example]: https://github.com/gpodder/gpodder/blob/master/share/gpodder/examples/hello_world.py
