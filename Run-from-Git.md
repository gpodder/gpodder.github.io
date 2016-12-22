If you are on Linux and want to try out the latest version of gPodder, it is easy to do by cloning from Git. You only need Python, PyGTK and Git installed, all other dependencies can be installed into the Git checkout.

## Do I need `root`, compile anything or install it system-wide?

As gPodder is written in Python, there is no need to compile anything or to install it into system directories (you do not need root). You can run it straight from a source checkout, this is also how gPodder's developers run it.

## Dependencies

* Python 2
* PyGTK
* Git

## Instructions

    git clone https://github.com/gpodder/gpodder.git
    cd gpodder
    python tools/localdepends.py         # To install dependencies
    python tools/create-desktop-icon.py  # Optional: Create Desktop icon 
    bin/gpodder                          # To directly launch from command line

## Updating

    cd gpodder
    git pull