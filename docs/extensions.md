Extensions are gPodder's mechanism for adding optional features and allowing easy customizability. Some extensions are already activated by default if you are running a specific environment (e.g. Ubuntu Unity support in gPodder 3 is implemented as an extension).

### Default Extensions Included With gPodder

The following extensions are included with gPodder 3:

-   [**Audio Converter**] - Transcode audio files to mp3/ogg
-   [**Enqueue in media players**] - Add a context menu item for enqueueing episodes in installed media players
-   **Gtk Status Icon** - Show a status icon for Gtk-based Desktops
-   **Minimize on start** - Minimizes the gPodder window on startup.
-   [**Normalize audio with re-encoding**] - Normalize the volume of audio files with normalize-audio
-   **Gtk+ Desktop Notifications** - Display notification bubbles for different events.
-   **Notification Bubbles for Windows** - 'Display notification bubbles for different events. (added in git master branch)
-   [**Rename episodes after download**] - Rename episodes to “<Episode Title>.<ext>” on download
-   [**Remove cover art from OGG files**] - removes coverart from all downloaded ogg files
-   **Convert video files to MP4 for Rockbox** - Converts all videos to a Rockbox-compatible format
-   **Sonos** - Stream podcasts to Sonos speakers
-   [**Tag downloaded files using Mutagen**] - Add episode and podcast titles to MP3/OGG tags
-   **Taskbar Progress** - Displays the progress on the Windows taskbar
-   **Subtitle Downloader for TED Talks** - Downloads .srt subtitles for TED Talks Videos
-   **Ubuntu App Indicator** - Show a status indicator in the top bar.
-   **Ubuntu Unity Integration** - Show download progress in the Unity Launcher icon.
-   [**Search for new episodes on startup**] - Starts the search for new episodes on startup
-   [**Video Converter**] - Transcode video files to avi/mp4/m4v
-   [**MPRIS Listener**] - listen to notifications from MPRIS-capable players and translate them to gPodder's [Media Player D-Bus API]

### How To Write Your Own Extension

*TODO*

[hello world extension example]

[**Audio Converter**]: extensions/audioconverter.md
[**Enqueue in media players**]: extensions/enqueueinmediaplayer.md
[**Normalize audio with re-encoding**]: extensions/normalizeaudio.md
[**Rename episodes after download**]: extensions/renameafterdownload.md
[**Remove cover art from OGG files**]: extensions/removeoggcover.md
[**Tag downloaded files using Mutagen**]: extensions/tagging.md
[**Search for new episodes on startup**]: extensions/searchepisodeonstartup.md
[**Video Converter**]: extensions/videoconverter.md
[**MPRIS Listener**]: extensions/mprislistener.md
[Media Player D-Bus API]: https://github.com/gpodder/gpodder/commit/ab48ea24f29a3d237396848520d27b3dba23635d
[hello world extension example]: https://github.com/gpodder/gpodder/blob/master/share/gpodder/examples/hello_world.py
