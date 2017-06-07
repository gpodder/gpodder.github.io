---
title: gPodder
subtitle: Media aggregator and [podcast](https://en.wikipedia.org/wiki/Podcast) client
logo: gpodder.png
---

gPodder is a simple, open source podcast client written in Python using GTK+. In development since 2005 with a proven, mature codebase.

{% assign version = site.data.gpodder.version %}
The latest version is {{version}}, released {{site.data.gpodder.date}}. Read the [release notes](http://blog.gpodder.org/).

### Get it

-   Windows: [gPodder {{version}}][win] (also as [ZIP][win-zip])<br>
    <small>You also need to install [32-bit Python 2.7][win-python] and [PyGTK 2.24][win-gtk]</small>
-   macOS: [gPodder {{version}}][mac]<br>
    <small>Already includes Python and PyGTK</small>
-   Linux/BSD: Install via the package manager<br>
    <small>Available in most distributions (Debian, Ubuntu, Fedora, ...)</small>
-   Source code: [github.com/gpodder/gpodder](https://github.com/gpodder/gpodder)

### Get help

Ask on the [mailing list](http://www.freelists.org/list/gpodder), report problems at the [issue tracker](https://github.com/gpodder/gpodder/issues) or read the [wiki](https://github.com/gpodder/gpodder/wiki).

[win]: http://sourceforge.net/projects/gpodder/files/windows/gpodder-{{version}}-setup.exe/download
[win-zip]: http://sourceforge.net/projects/gpodder/files/windows/gpodder-{{version}}-win32.zip/download
[win-python]: https://www.python.org/ftp/python/2.7.12/python-2.7.12.msi
[win-gtk]: http://ftp.gnome.org/pub/GNOME/binaries/win32/pygtk/2.24/pygtk-all-in-one-2.24.2.win32-py2.7.msi
[mac]: https://sourceforge.net/projects/gpodder/files/macosx/gPodder-{{version}}_0.zip/download