---
title: macOS
---

gPodder is now available in MacPorts for installing on Mac OS X. Thanks to **Eric Le Lay** who has created the Portfile for gPodder.

Helpful resources
-----------------

-   [MacPorts FAQ](http://trac.macports.org/wiki/FAQ)

Installing MacPorts
-------------------

You can obviously skip this step if you have already installed MacPorts. Advanced users might also opt to install MacPorts from source instead of using the .dmg installer.

1.  Go to <http://www.macports.org/install.php>
2.  Install the "dmg" disk image for your version of Mac OS X
3.  Get yourself some coffee (or tea, if you prefer) - finishing the installation takes a while

Installing gPodder using the "port" command
-------------------------------------------

After installing MacPorts, you should have the `port` command available:

1.  Open a Terminal window
2.  Enter "sudo port install gpodder" (or `sudo` `port` `install` `gpodder` `+quartz` - see Alternative: Native OSX GTK+ section bellow)
3.  Enter your password (it won't be displayed, just type it and hit enter)
4.  Get yourself some coffee and watch an episode or your favourite TV show

Depending on how much you have installed from MacPorts before, the installation of gPodder can be quicker or slower (if you start afresh, it will take longer, because it has to build more dependencies - if you have installed things like GTK+, Python, PyGTK, etc.., it should be done soon).

Installing gPodder using a MacPorts GUI frontend
------------------------------------------------

You can also install gPodder using one of the GUI frontends for MacPorts:

-   [MacPortsGUI](http://trac.macports.org/wiki/MacPortsGUI)
-   [Porticus](http://porticus.alittledrop.com/)

Troubleshooting
---------------

### ImportError: No module named gpodder

This has happend to me after installing gPodder using MacPorts. To fix it, edit the file `/opt/local/bin/gpodder`:

-   Change the first line to

`#!/opt/local/bin/python2.6`

-   Replace the section that tries to import the D-Bus modules with:

`sys.path.insert(0, '/opt/local/lib/python2.6/site-packages')`
`have_dbus = False`

(Message from the OS X maintainer) I filed a bug to myself to fix this - it should be committed soon : <http://trac.macports.org/ticket/22522>

Don't worry, it is FIXED now !

### D-Bus error: Not enough memory

This error happens when the D-Bus session daemon cannot be started. You can fix this by editing `/opt/local/lib/python2.6/site-packages/gpodder/gui.py`:

-   In the `try` block that imports the D-Bus module, add this code:

`raise ImportError('No D-Bus on Mac OS X')`

-   OR install dbus in macports :

`sudo` `port` `install` `dbus`

the services are disabled by default.

Load and enable the system bus :

`sudo` `launchctl` `load` `-w` `/Library/LaunchDaemons/org.freedesktop.dbus-system.plist`

You have to load org.freedesktop.dbus-session.plist as normal user, but you must enable it first :

`sudo` `vi` `/Library/LaunchAgents/org.freedesktop.dbus-session.plist`

(remove the disabled = true entry at the begining of the file)

`launchctl` `load` `/Library/LaunchAgents/org.freedesktop.dbus-session.plist`

Now dbus will be launched at startup, and gpodder should find it !

Alternative: Native OSX GTK+
----------------------------

If you would like a native application, the safest path is to select the quartz variant of gpodder

`  ``sudo` `port` `install` `gpodder` `+quartz`

Note that this will not rebuild the full GTK stack to use native (aka Quartz) rendering if gtk is already installed. So the command can fail along the way. If it happens, you'll have to reconsider using the quartz variant or reinstall gtk2 and everything that depends on it (and a few packages it depends on, like cairo, pango, etc.). I do not know of a way to have a native GTK stack AND an X11 GTK stack active at the same time.

If you want to use a standalone build of everything (i.e. not use MacPorts), you may want to try [this](https://github.com/elelay/gpoder-osx-bundle/wiki/Using). You'll get a nice gPodder.app native application, that **HAS NOT BEEN TESTED**.

For background, you may be interested in : - [this mailing list post](http://www.freelists.org/post/gpodder/HOWTO-Run-gPodder-in-Mac-OS-X) for instructions.

` You're on your own, and the instructions are probably not up-to-date.`
