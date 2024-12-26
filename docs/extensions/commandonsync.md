---
title: Run a Command on Sync
---

Run a predefined external command upon sync completion.

-   [Extension Source](https://github.com/gpodder/gpodder/blob/master/share/gpodder/extensions/command_on_sync.py)


| setting            | value      | description                                 | version           |
|--------------------|------------|---------------------------------------------|-------------------|
| command            | string     | command to execute (passed to the shell)    | git master branch |

Introduction
-----------

One might want to run an external program when all podcast episodes get synchronized to external database (refresh a player's database or enqueue the episode, download episode statistics, run other device-related program like Last.FM scrobbler, etc.). This extension makes it possible to execute any command.

Usage
-----

1. In the Extensions tab under Preferences, check "Run a Command on Sync" (in the "Post Sync" section).
2. In the Advanced Configuration (**Edit Configuration** button), define the `extensions.command_on_sync.command`
    entry to the command you want to run.

If the command is a bit long, write a wrapper script. You can also directly edit
`$GPODDER_HOME/Settings.json` to refine your command.

Example Commands
--------------

### Linux

```
zenity --info --width=600 --text="All episodes synchronised"
```

displays all variables in a dialog window (requires zenity).

### Scrobble playback log file to Last.FM (requires rb-scrobbler)

```
rb-scrobbler -f $SCROBBLER_LOG_FILE -n delete-on-success
```

You can obtain rb-scrobbler on [Github](https://github.com/jeselnik/rb-scrobbler).
