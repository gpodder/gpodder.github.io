---
title: gPodder
subtitle: Media aggregator and podcast client
logo: gpodder.png
---

<style>
ul {
    padding-left: 10px;
}

ul li {
    padding: 8px;
    list-style: none;
    color: #333;
}
</style>

gPodder is a simple, open source [podcast](https://en.wikipedia.org/wiki/Podcast) client written in Python using GTK+. In development since 2005 with a proven, mature codebase.

{% assign version = site.data.gpodder.version %}
The latest version is <span id="latest-version">{{version}}</span>, released <span id="release-date">{{site.data.gpodder.date}}</span>. Read the [release notes](https://github.com/gpodder/gpodder/releases).

### Get it

-   Windows: [gPodder {{site.data.windows.version}}][win] (also as [ZIP][win-zip])<br>
    <small>You also need to install [32-bit Python 2.7.9+][win-python] and [PyGTK {{site.data.windows.pygtkVersion}}][win-gtk]</small>
-   macOS: [gPodder {{site.data.macos.version}}][mac]<br>
    <small>Already includes Python and PyGTK ([older versions on sourceforge][sourceforge])</small>
-   Linux/BSD: In your distro, or [run from Git][]<br>
    <small>Available in Debian, Ubuntu, Fedora, FreeBSD Ports, ...</small>
-   Source code: [github.com/gpodder/gpodder](https://github.com/gpodder/gpodder)

### Get help

Ask on the [mailing list](http://www.freelists.org/list/gpodder), report problems at the [issue tracker](https://github.com/gpodder/gpodder/issues) or read the [documentation](docs/).

[win]: https://github.com/gpodder/gpodder/releases/download/{{site.data.windows.version}}/gpodder-{{site.data.windows.version}}-setup.exe
[win-zip]: https://github.com/gpodder/gpodder/releases/download/{{site.data.windows.version}}/gpodder-{{site.data.windows.version}}-win32.zip
[win-python]: https://www.python.org/ftp/python/{{site.data.windows.pythonVersion}}{{site.data.windows.pythonPatch}}/python-{{site.data.windows.pythonVersion}}{{site.data.windows.pythonPatch}}.msi
[win-gtk]: http://ftp.gnome.org/pub/GNOME/binaries/win32/pygtk/{{site.data.windows.pygtkVersion}}/pygtk-all-in-one-{{site.data.windows.pygtkVersion}}{{site.data.windows.pygtkPatch}}.win32-py{{site.data.windows.pythonVersion}}.msi
[mac]: https://github.com/gpodder/gpodder/releases/download/{{site.data.macos.version}}/macOS-gPodder-{{site.data.macos.version}}.zip
[run from Git]: https://github.com/gpodder/gpodder/wiki/Run-from-Git
[sourceforge]: https://sourceforge.net/projects/gpodder/files/macosx