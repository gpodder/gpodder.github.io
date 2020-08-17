---
title: macOS
---

gPodder is now available as:
 - a macOS Application (Download from [Here](../index.md#get-it)).
 - Homebrew Cask

If you're not already using Homebrew, the macOS application download is the recommended way to install gPodder.

Simply double-click to unzip the application, then copy `gPodder.app` to your `/Applications` folder.

Otherwise, using Homebrew, run `brew cask install gpodder; xattr -d com.apple.quarantine /Applications/gPodder.app`

Debugging gPodder on macOS
-------------------------

1. Ensure gPodder isn't running
2. Start the Terminal application
3. enter `/Applications/gPodder.app/Contents/MacOS/gpodder -v` and press the Enter key

You’ll see all the debug information you want.

Building the macOS application yourself
-----------------------------------

Code to generate the macOS application is hosted [here](https://github.com/gpodder/gpodder-osx-bundle).

Old (3.9.x) Versions
------------------

macOS releases were first hosted on sourceforge .
See the archive [here](https://sourceforge.net/projects/gpodder/files/macosx).
