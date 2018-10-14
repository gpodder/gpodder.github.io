---
title: Windows
---

Changing the gPodder Home/Download Folders on Windows
--------------------------------------
See the [User Manual](user-manual#changing-the-downloads-folder-location-and-the-gpodder-home-folder) for background on changing the gPodder Home and Download folders.


Debugging gPodder on Windows
-------------------------

Both the portable and installer version of gPodder come with a console version for debug messages.
To launch it:

1. Choose Start > Run... or use the Win-R shortcut
2. enter cmd and press OK
3. navigate to the gPodder binary directory
  (`C:\Program Files (x86)\gPodder\bin` for the installer version,
  `gpodder-portable-x.y.z\data\bin` for the portable version)
4. drag and drop gpodder-cmd.exe from the windows explorer to the console window
5. add a space and `-v` to the text and press the Enter key

You'll see all the debug information you want.


gPodder 3 on Windows (from Git)
-------------------------------

See the Windows installer [build documentation](https://github.com/gpodder/gpodder/blob/master/tools/win_installer/README.rst).


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

**Warning: this section has not been updated for gPodder 3.10.0 and later!**

This is some hackery to get synchronization for an MP3 player to work

-   Save build to `c:\Program` `Files\gpodder-win32_20090512`
-   Install eyeD3 in `lib\site-packages`
-   Install oggdec in `bin` and copy it to `bin\oggdec` also. (The unix-specific code searches for the executable by this name.)
-   To read OGG tags, install Vorbis Tools

<http://www.vorbis.com/files/1.0.1/windows/vorbis-tools-1.0.1-win32.zip> in the bin directory.
