---
title: Run a Command on Download
---

Run a predefined external command upon download completion.

-   [Extension Source](https://github.com/gpodder/gpodder/blob/master/share/gpodder/extensions/command_on_download.py)


| setting            | value      | description                                 | version           |
|--------------------|------------|---------------------------------------------|-------------------|
| command            | string     | command to execute (passed to the shell)    | git master branch |

Introduction
-----------

One might want to run an external program on episode download (refresh a player's database or enqueue the episode,
flash a red lamp, etc.). This extension makes it possible to execute any command, providing episode's details
as environment variables.

Usage
-----

1. In the Extensions tab under Preferences, check "Run a Command on Download" (in the "Post Download" section).
2. In the Advanced Configuration (**Edit Configuration** button), define the `extensions.command_on_download.command`
    entry to the command you want to run.

I advise you to write a wrapper script if the command is a bit long. You can also directly edit
`$GPODDER_HOME/Settings.json` to refine your command.

Available Environment Variables
----------------------------

Check the extension's code for the most up to date list, but there are curently:

- **filename**: full path to the downloaded episode
- **playlist_title**: podcast name - episode title (publication date)
- **podcast**: podcast name
- **published**: episode publication date in `YYYY-MM-DD HH:mm` format
- **section**: podcast section
- **title**: episode title


Example Commands
--------------

### Linux

```
zenity --info --width=600 --text="file=$filename podcast=$podcast title=$title published=$published section=$section playlist_title=$playlist_title"
```

displays all variables in a dialog window (requires zenity).

### Cross Platform

```
python -c "import os;import gi; gi.require_version('Gtk', '3.0'); from gi.repository import Gtk; win = Gtk.Window(); l = Gtk.Label(label='{filename} downloaded'.format(**os.environ)); win.add(l); win.connect('delete-event', Gtk.main_quit); win.show_all(); Gtk.main()"
```

opens a window with the download path.


### Enqueue in MPD

```
mpc add "$filename"
```
