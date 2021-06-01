---
title: YouTube
---

These are instructions to subscribe to user channels in YouTube - 3.10.20 and later.


Subscribe to channels
---------------------

The URL for channel or video pages can be used to subscribe to a channel.


Built-in support
----------------

The built-in YouTube support is limited to the 15 most recent videos posted on the channel, and can not download DRM or age-restricted videos. Live streams can be streamed while live, but can only be downloaded after they have ended, usually several hours later. All downloadable videos can be streamed.

Changes to YouTube's API can prevent channel updates or episode downloads until fixed and a new gPodder release is made available. The [YouTube-DL extension](https://gpodder.github.io/docs/extensions/youtubedl.html) can often be used to allow continued access to YouTube while the built-in support is not working.


YouTube-DL extension
--------------------

YouTube-DL can be used to download higher resolution videos as well as DRM and age-restricted content.

The `extensions.youtube-dl.manage_channel` setting uses YouTube-DL to update channels, enabling access to all episodes on the channel, bypassing the 15 episode limit of the built-in support. It does however take significantly longer to update channels using this feature.

The `extensions.youtube-dl.manage_downloads` setting uses YouTube-DL to download all episodes. In the future, it will be possible to stream with this enabled and a video player with YouTube-DL such as MPV. But for now, this setting must be disabled to stream episodes.

When `extensions.youtube-dl.manage_downloads` is disabled, the right-click menu for episodes has a `Download with Youtube-DL` action. This allows episodes to still be streamed, but requires manual downloading of each episode if YouTube-DL formats are wanted.

On Linux, YouTube-DL can be updated externally to fix issues that occur after YouTube API changes. On Windows, a newer GIT version (if available) can be downloaded from <https://ci.appveyor.com/project/elelay/gpodder/build/artifacts> to update the bundled copy of YouTube-DL. It is not yet possible to upgrade the bundled copy in the Mac bundle.

More information about the YouTube-DL extension can be found at <https://gpodder.github.io/docs/extensions/youtubedl.html>.


Formats
-------

The `Video` tab in `Preferences` has options to select the download and live streaming (HLS) formats. HLS formats are only available during a live stream, and streaming of non-livestream episodes always uses the download format.

The built-in support is limited to MP4 360p (18) and MP4 720p (22) formats. It can also download the audio-only formats: M4A 128k (140), WEBM 50k (249), WEBM 70k (250), and WEBM 160k (251). They are not yet fully supported and must be added to the `youtube.preferred_fmt_ids` setting, separated by commas, and then choosing the custom formats option.

The formats labelled with `youtube-dl` only work with YouTube-DL and fall-back to the above formats when built-in support is used. The `best` formats are also not yet supported and must be enabled like the above audio formats.

WEBM formats fall-back to MP4 when a WEBM format is not available at the desired resolution.
