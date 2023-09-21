---
title: Windows
---

Supported Version
---------------

gPodder is tested on **Windows 10**, but it should also work on Windows 7 and later.

gPodder 3.11.2 and later is [known](https://github.com/gpodder/gpodder/issues/1540)
not to work on Windows 7. Although, it might be possible to build gPodder yourself
using an older version of msys2.

gPodder 3.10.9 and later is [known](https://www.freelists.org/post/gpodder/gpodder-Digest-V9-17)
not to work on Windows XP.

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

1.  Install Python from <http://www.python.org/>
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


Switching to a dark theme variant
---------------------------------

To use a dark theme variant, add the `gtk-application-prefer-dark-theme = true` line to your `settings.ini`:

 1. Locate the `etc\gtk-3.0\settings.ini` file in your gPodder installation (for instance `C:\gpodder-3.10.3-portable\data\etc\gtk-3.0\settings.ini`);
 2. open it with notepad;
 3. add a new line reading `gtk-application-prefer-dark-theme = true`

Example settings.ini:

```
[Settings]
gtk-font-name = Segoe UI 10
gtk-application-prefer-dark-theme = true
```


Changing the theme
------------------

It is possible to switch gPodder to any Gtk3-compatible theme
by copying it to C:\Users\YOUR_USER\.themes and referencing it by name in GPODDER_INSTALL_DIR\etc\gtk-3.0\settings.ini.

For instance, to use the low contrast theme Equilux:

 1. I created a .themes folder in my user directory C:\Users\IEUser
 2. I downloaded [Equilux-compact.tar.xz](https://www.pling.com/p/1182169/) and extracted in C:\Users\IEUser\.themes
 3. I edited `C:\gpodder-3.10.3-portable\data\etc\gtk-3.0\settings.ini` to look like this:

```
[Settings]
gtk-font-name = Segoe UI 10
gtk-theme-name = Equilux-compact
```
