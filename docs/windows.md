---
title: Windows
---

Please Note
-----------

These directions do not work, and they need to be updated.

gPodder 3 on Windows (from Git)
-------------------------------

gPodder (&gt;= 3.0.0) will automatically install the following two dependencies when needed, but if you want, you can already pre-install these packages, so that gPodder doesn't need to download them on first start:

1.  Install Python 2.7 from <http://www.python.org/>
2.  Install the PyGTK All-in-one installer from <http://www.pygtk.org/>

You can run the latest development version of gPodder on Windows using these simple instructions:

1.  Install msysgit from <http://code.google.com/p/msysgit/>
2.  Open "Git Bash" from the start menu
    1.  `git` `clone` [`git://github.com/gpodder/gpodder`](git://github.com/gpodder/gpodder)
    2.  `cd` `gpodder`
    3.  `git` `checkout` `tres`

3.  Get additional modules (drop these into `src/`):
    1.  mygpoclient - <http://thp.io/2010/mygpoclient/>
    2.  feedparser - <http://code.google.com/p/feedparser/>
    3.  dbus - in `tools/fake-dbus-module/`

4.  Copy `gpodder.exe` and `gpo.exe` from `tools/win32-launcher/` to the checkout folder
5.  Start gPodder by running `gpodder.exe` (for the GUI) or `gpo.exe` (for the CLI)

Panucci on Windows
------------------

[Panucci](http://panucci.garage.maemo.org/) is a resuming podcast and audiobook player, originally developed for Maemo and Linux, but it's also usable on Windows.

1.  Install Python 2.6 from <http://www.python.org/>
2.  Install PyCairo, PyGObject and PyGTK from <http://www.pygtk.org/downloads.html>
3.  Install the GTK+ bundle from <http://ftp.gnome.org/pub/GNOME/binaries/win32/gtk+/>
4.  Install GStreamer (GPL) + PyGSt from <http://www.gstreamer-winbuild.ylatuya.es/doku.php?id=download>
5.  Add the `bin/` folders for both GTK+ and GStreamer to your PATH variable (Win+Break, Advanced, Environment variables)
6.  Grab the source code from <http://nikosapi.org/git/panucci/> using Git (or use a [snapshot](http://nikosapi.org/git/panucci/snapshot/master.zip))
7.  Grab [panucci-win32.patch](http://khan.thpinfo.com/~thp/tmp/panucci-win32.patch) and apply it (e.g. using [patch](http://gnuwin32.sourceforge.net/packages/patch.htm))
8.  Grab a Mutagen release from <http://code.google.com/p/mutagen/> and extract it
9.  Copy the `mutagen/` folder from the Mutagen release to `src/` in your Panucci folder
10. Open a console window and enter: `python` `bin/panucci`
11. Have fun :)

Alternatively, do the first 5 steps from above, make sure that Python is available in your PATH and then download [panucci-win32-20091114.zip](http://khan.thpinfo.com/~thp/tmp/panucci-win32-20091114.zip).

**Additional hint:** If you want to have proper Windows themeing, copy `share/themes/MS-Windows/gtk-2.0/gtkrc` to `etc/gtk-2.0/` in the folder where you installed GTK+.

MP3 Synchronization
-------------------

This is some hackery to get synchronization for an MP3 player to work

-   Save build to `c:\Program` `Files\gpodder-win32_20090512`
-   Install eyeD3 in `lib\site-packages`
-   Install oggdec in `bin` and copy it to `bin\oggdec` also. (The unix-specific code searches for the executable by this name.)
-   To read OGG tags, install Vorbis Tools

<http://www.vorbis.com/files/1.0.1/windows/vorbis-tools-1.0.1-win32.zip> in the bin directory.
