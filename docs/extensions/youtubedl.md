---
title: Youtube-dl
---

This extension uses the [youtube-dl](http://ytdl-org.github.io/youtube-dl/) or the
[yt-dlp](https://github.com/yt-dlp/yt-dlp) package to **download episodes** and/or
**refresh subscriptions**.

It will let you download episodes in [any format available from Youtube](#download).

It will let you see [more than the last 15 episodes](#subscriptions) in the channel or playlist.

This extension overrides Youtube subscriptions globally so you don't have to enable it podcast by podcast.


## Dependencies

The `yt-dlp` package is already provided in the Windows and macOS prebuilt applications.

If you need to install it manually, `pip install youtube_dl` or `pip install yt-dlp`.


## Downloading episodes with youtube-dl         {#download}

The main advantage of this extension is to use youtube-dl to download formats not available natively.

For instance with youtube-dl you can **download the audio only**:

 1. Go to *Preferences* > *Extensions* to activate the youtube-dl extension;
 2. Press the *Edit config* button in *Preferences*
 3. Search for *youtube* and set the `youtube.preferred_fmt_ids` parameter to `bestaudio[ext=ogg], bestaudio`.
 4. Set `youtube.preferred_fmt_id` to 0 to enable the custom format set in the previous step

`youtube.preferred_fmt_ids` takes a list of format strings separated by comma:
`bestaudio[ext=ogg],bestaudio` is translated to youtube-dl format `bestaudio[ext=ogg]/bestaudio`, meaning preferably
the best audio quality in Ogg Vorbis format, then any audio-only if ogg is not available.

See <https://github.com/ytdl-org/youtube-dl#format-selection> for details
about the youtube-dl format specification and for more examples.


## Managing subscriptions with youtube-dl      {#subscriptions}

Youtube-dl will load the page for your subscription (channel, playlist, ...) and find all
videos there. This way you will get all episodes, not only the last 15 like in Youtube's own
RSS feed.

The major drawback is that youtube-dl is **very slow** to get this information because
it has to download and parse each video page.

Note that the extension will only parse *new* videos so it's faster on refresh than when subscribing
for the first time.

It is possible to go back to the limited but fast RSS feed by setting `extensions.youtube-dl.manage_channels`
to false.

## Settings

| setting                                   | value          | description                                                                   |
|-------------------------------------------|----------------|-------------------------------------------------------------------------------|
| extensions.youtube-dl.manage_channels     | **true**/false | false to use Youtube's RSS feed (faster but only 15 episodes)                 |
| extensions.youtube-dl.manage_downloads    | **true**/false | false to download using built-in class (if youtube-dl doesn't work)           |

gPodder 3.11.0 added a preferences page for youtube-dl to better find these settings.
The `manage_channel` setting is listed as "Parse YouTube channel feeds ..."
and the `manage_downloads` setting is listed as "Download all supported episodes ...".

youtube-dl extension will use the proxy set in [gPodder proxy settings](../user-manual.md#using-a-http-or-socks-proxy-server).

## Read settings from youtube-dl or yt-dlp config file

gPodder 3.11.6 can load settings from the same config file used by the command line tool, and other tools such as mpv.
The file can be found at `${XDG_CONFIG_HOME}/yt-dlp/config` on Linux/macOS, and `${APPDATA}/yt-dlp/config` on Windows.
A list of more config file locations are available at https://github.com/yt-dlp/yt-dlp#configuration.

The extension's preferences page has a checkbox that must be enabled to load the config file.
Please uncheck it to verify extension related errors are not caused by settings in your config file.

Some settings are overridden by gPodder, such as `-f` and `--format`.

Links:

- [Extension Source](https://github.com/gpodder/gpodder/blob/master/share/gpodder/extensions/youtube-dl.py)
