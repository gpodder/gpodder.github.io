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

-   Windows: [gPodder {{site.data.windows.version}} installer][win] (also as [portable app][win-portable])<br>
    <small>Already includes Python 3, Gtk 3</small>
-   macOS: [gPodder {{site.data.macos.version}}][mac]<br>
    <small>Already includes Python 3, Gtk 3</small>
-   Linux/BSD: In your distro, as [Flatpak][flatpak], [Ubuntu ppa][ppa] or [run from Git](docs/run-from-git.md)<br>
    <small>Available in Debian, Ubuntu, Fedora, FreeBSD Ports, ...</small>
-   Sailfish OS: from [OpenRepos](https://openrepos.net/content/keeperofthekeys/gpodder)<br>
    <small>a flavor of gPodder for mobiles running Sailfish OS 1.0.4.20 or later.</small>
-   Source code: [github.com/gpodder/gpodder](https://github.com/gpodder/gpodder)
-   Older releases are available from [github][releases].

### Get help

- Read the [documentation](docs/)
- Ask on the [mailing list](http://www.freelists.org/list/gpodder)
- Report problems at the [issue tracker](https://github.com/gpodder/gpodder/issues)

[win]: https://github.com/gpodder/gpodder/releases/download/{{site.data.windows.version}}/windows-gpodder-{{site.data.windows.version}}-installer.exe
[win-portable]: https://github.com/gpodder/gpodder/releases/download/{{site.data.windows.version}}/windows-gpodder-{{site.data.windows.version}}-portable.exe
[mac]: https://github.com/gpodder/gpodder/releases/download/{{site.data.macos.version}}/macOS-gPodder-{{site.data.macos.version}}.zip
[releases]: https://github.com/gpodder/gpodder/releases
[ppa]: https://launchpad.net/~gpodder/+archive/ubuntu/ppa
[flatpak]: https://flathub.org/apps/details/org.gpodder.gpodder
