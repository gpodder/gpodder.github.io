---
title: Filter episodes to prevent automatic download
---

The **Filter** tab on the per-channel **Podcast Settings** dialog can be used to block all episodes
or specific episodes for a channel. Blocking marks episodes as old, preventing automatic download.

Selecting **Block** and leaving its text field empty will block all episodes for the channel.
Entering text performs a partial case-sensitive match on the episode title. The **Ignore Case**
checkbox performs a case-insensitive match and the **Regular Expression** checkbox treats the text
field as a regular expression, enabling complex matches.

Selecting **Except** is used to override blocking for certain types of episodes. The most common
case would be when blocking all episodes, and only unblocking the ones that match a pattern.
A specific category of episodes could also be blocked and this would unblock episodes in the
category that contain a keyword.

It is not recommended to select **Except** and leave its text field empty, as this effectively
disables all blocking.

The **Filter episodes now** button can be used to test changes to filters by applying them
immediately, without needing to update the channel.

Links:

-   [Extension Source](https://github.com/gpodder/gpodder/blob/master/share/gpodder/extensions/filter.py)
