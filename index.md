---
title: gPodder
subtitle: Media aggregator and [podcast](https://en.wikipedia.org/wiki/Podcast) client
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

gPodder is a simple, open source podcast client written in Python using GTK+. In development since 2005 with a proven, mature codebase.

{% assign version = site.data.gpodder.version %}
The latest version is {{version}}, released {{site.data.gpodder.date}}. Read the [release notes](http://blog.gpodder.org/).

### Get it

-   Windows: [gPodder {{site.data.windows.version}}][win] (also as [ZIP][win-zip])<br>
    <small>You also need to install [32-bit Python {{site.data.windows.pythonVersion}}][win-python] and [PyGTK {{site.data.windows.pygtkVersion}}][win-gtk]</small>
-   macOS: [gPodder {{site.data.macos.version}}][mac]<br>
    <small>Already includes Python and PyGTK</small>
-   Linux/BSD: [Ubuntu PPA][], [AppImage][], or [run from Git][]<br>
    <small>Also available in Debian, Ubuntu, Fedora, FreeBSD Ports, ...</small>
-   Source code: [github.com/gpodder/gpodder](https://github.com/gpodder/gpodder)

### Get help

Ask on the [mailing list](http://www.freelists.org/list/gpodder), report problems at the [issue tracker](https://github.com/gpodder/gpodder/issues) or read the [documentation](docs/).

[win]: http://sourceforge.net/projects/gpodder/files/windows/gpodder-{{site.data.windows.version}}-setup.exe/download
[win-zip]: http://sourceforge.net/projects/gpodder/files/windows/gpodder-{{site.data.windows.version}}-win32.zip/download
[win-python]: https://www.python.org/ftp/python/{{site.data.windows.pythonVersion}}{{site.data.windows.pythonPatch}}/python-{{site.data.windows.pythonVersion}}{{site.data.windows.pythonPatch}}.msi
[win-gtk]: http://ftp.gnome.org/pub/GNOME/binaries/win32/pygtk/{{site.data.windows.pygtkVersion}}/pygtk-all-in-one-{{site.data.windows.pygtkVersion}}{{site.data.windows.pygtkPatch}}.win32-py{{site.data.windows.pythonVersion}}.msi
[mac]: https://sourceforge.net/projects/gpodder/files/macosx/gPodder-{{site.data.macos.version}}{{site.data.macos.patch}}.zip/download
[Ubuntu PPA]: https://launchpad.net/~thp/+archive/ubuntu/gpodder
[AppImage]: https://bintray.com/probono/AppImages/gPodder
[run from Git]: https://github.com/gpodder/gpodder/wiki/Run-from-Git
