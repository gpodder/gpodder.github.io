---
title: Run from Git
---

If you are on Linux and want to try out the latest version of gPodder, it is easy to do by cloning from Git. You only need Python, PyGObject3, Gtk3 and Git installed, all other dependencies can be installed into the Git checkout.

## Do I need `root`, compile anything or install it system-wide?

As gPodder is written in Python, there is no need to compile anything or to install it into system directories (you do not need root). You can run it straight from a source checkout, this is also how gPodder's developers run it.

## Dependencies

* Git
* Python 3.5+
* Requests 2.24+
* Python D-Bus bindings or `tools/fake-dbus-module/`
* podcastparser
* mygpoclient

## Gtk3 Dependencies

* Gtk 3.16+
* PyGObject 3.22+
* python bindings: gir1.2-gtk-3.0 python3-cairo python3-gi-cairo on Debian

## Optional Dependencies

* html5lib
* mutagen
* yt-dlp

## Instructions

    git clone https://github.com/gpodder/gpodder.git
    cd gpodder
    # To install required and optional dependencies
    # (not including git, python or gtk3 dependencies)
    python3 -m pip install -r tools/requirements.txt         # as root
    python3 -m pip install --user -r tools/requirements.txt  # as user
    # Optional: Create desktop icon
    python3 tools/create-desktop-icon.py

    # To directly launch from command line
    bin/gpo                               # cli client
    bin/gpodder                           # gtk3 client

## Updating

    cd gpodder
    git pull
