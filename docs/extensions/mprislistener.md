---
title: MPRIS Listener
---

Listen to notifications from MPRIS-capable players and translate them to gPodder's [Media Player D-Bus API](https://github.com/gpodder/gpodder/blob/ab48ea24f29a3d237396848520d27b3dba23635d/src/gpodder/player.py#L26).

-   [Extension Source](https://github.com/gpodder/gpodder/blob/master/share/gpodder/extensions/mpris-listener.py)
-   [Extension Source History (prior to inclusion in gPodder)](https://bitbucket.org/dov/gpodder-mpris-listener)

Introduction
------------

gPodder defines the [Media Player D-Bus API](https://github.com/gpodder/gpodder/blob/ab48ea24f29a3d237396848520d27b3dba23635d/src/gpodder/player.py#L26) for media players to use for reporting their current playback position over D-Bus. gPodder listens to these notifications, and uses that information, for example, to store an episode's last-played position. This, in turn, can be used to determine whether an episode is "finished" (fully played), or to resume subsequent playback from the last-played position.

Unfortunately, to the best of my knowledge, only one media player ([Panucci](https://github.com/gpodder/panucci)) implements this API. In theory, plugins could be written to implement this API in other players -- there's even a GSoC Idea to do this -- but as far as I know, no such plugins have yet been written.

On the other hand, the [Media Player Remote Interfacing Specification](http://www.freedesktop.org/wiki/Specifications/mpris-spec/) (MPRIS) seems to be more widely adopted, while offering similar functionality (and then some). It, too, runs over D-Bus, and a number of high-profile media players already implement it. So the idea of this gPodder extension is to listen for the MPRIS notifications and translate them, where appropriate, to gPodder's native Media Player D-Bus API. In this way, we gain support for all MPRIS-capable players with a single gPodder extension, rather than having to implement -- within each media player separately --a gPodder-oriented plugin.

Related gPodder features
------------------------

The ability to track an episode's last-played position plays nicely with a number of other optional gPodder features:

-   The last-played position can be displayed in the episodes list (make sure "duration" is checked in View -&gt; Visible columns).
-   Based on the last-played position, gPodder can determine when an episode is "finished" (fully played). This, in turn, can be used for automatically deleting only finished episodes, but not partially-played ones (in the Clean-up tab of Preferences, uncheck "Remove played episodes even if unfinished").
-   The last-played position is synced with gpodder.net, allowing you to start listening to an episode on one device, and resume from the last-played position on another device. Note that resuming playback from a given position is not yet fully supported: it works automatically on the n900; and more generally, can be provided to players which support such an option by specifying "%p" as part of a [custom audio player command](../user-manual.md#general-preferences).

For more background, see [this discussion](http://article.gmane.org/gmane.network.syndication.podcast.gpodder.devel/2403) (from nearly three years ago) on the mailing list. Most of the issues discussed there were already working at the time, or fixed soon thereafter. The main feature that was missing until now is the ability to receive the last-played position from many players in the first place.

Usage
-----

In the Extensions tab under Preferences, check "MPRIS Listener" (in the "Desktop Integration" section).

Status
------

I have been using this on my own system for a few months now, and it works quite well. I have tested only with VLC (which supports MPRIS starting around 2.0). I imagine each player will have its own quirks, so expect new issues to turn up.

Even in my limited testing, there are a few issues I am aware of:

-   No tests!
-   Currently logs *a lot* of debug (if gPodder is started with `-v`). This should probably be cleaned-up, though I still want to be able to collect logs for diagnosing issues.
-   Currently, an error is logged when VLC closes. This is not a real problem, but I haven't yet looked into why the error is reported.
-   Currently only a single playing item is supported. This means that if you start playing item A, then play item B (say, in a different instance of the player), and then resume A, the listener gets confused. I haven't yet looked into the details of this.
-   If turned on in the middle of a playing item, no notifications are received for the currently playing item. (This may be related to the previous issue.)
-   End positions are occasionally reported "incorrectly": currently, the listener ignores end positions which are more than a few seconds past the total length of the item (as reported by the player). This *does* appear to occasionally happen, though. I have not looked into the details much.