---
title: Run from Git
---

If you want to try out the latest version of gPodder or help develop, it is easy to clone from Git. You only need Python, PyGObject3, Gtk3 and Git installed, all other dependencies can be installed into the Git checkout.

## Do I need `root`, compile anything or install it system-wide?

As gPodder is written in Python, there is no need to compile anything or to install it into system directories (you do not need root). You can run it straight from a source checkout, this is also how gPodder's developers run it.

## Dependencies

* Git
* Python 3.7+
* Requests 2.24+
* Python D-Bus bindings or `tools/fake-dbus-module/`
* podcastparser
* mygpoclient

## Gtk3 Dependencies

* Gtk 3.16+
* PyGObject 3.22+
* python bindings: gir1.2-gtk-3.0 python3-cairo python3-gi-cairo on Debian

## Optional Dependencies

Defined in pyproject.toml:

* eyed3
* PySocks
* html5lib
* mutagen
* filelock
* pillow
* yt-dlp

## Instructions

First time setup:

    git clone https://github.com/gpodder/gpodder.git
    cd gpodder

    # Optional: create virtual environment (required on MacOS)
    python3 -m venv ./.venv
    # load virtual environment, if using one
    source ./.venv/bin/activate

    # Select one of the following four steps to install dependencies:
    # (does not install git, python or gtk3 dependencies)

    # required dependencies only (as root, or if in virtual environment)
    python3 -m pip install .
    # required dependencies only (as user)
    python3 -m pip install --user .
    # required and optional dependencies (as root, or if in virtual environment)
    python3 -m pip install '.[eyed3,gui,html5lib,mutagen,coverart,yt-dlp]'
    # required and optional dependencies (as user)
    python3 -m pip install --user '.[eyed3,gui,html5lib,mutagen,coverart,yt-dlp]'

    # Optional: Create desktop icon
    python3 tools/create-desktop-icon.py

    # Windows and Mac: add the fake dbus module to the python path
    export PYTHONPATH=./tools/fake-dbus-module/

    # To directly launch from command line
    bin/gpo                               # cli client
    bin/gpodder                           # gtk3 client

The next time you wish to run gPodder, do the following:

    cd gpodder

    # if using a virtual environment
    source ./.venv/bin/activate

    # if on Windows or Mac
    export PYTHONPATH=./tools/fake-dbus-module/

    ./bin/gpodder

## Updating

    cd gpodder
    git pull
