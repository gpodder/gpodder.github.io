---
title: libmygpo-qt
---

General
-------

### General Information

libmygpo-qt is a Qt/C++ library wrapping the [gpodder.net Webservice](http://wiki.gpodder.org/wiki/Web_Services). It is currently used in Amarok & Clementine to retrieve a directory of podcasts & to synchronize podcast subscriptions with [gpodder.net](http://wiki.gpodder.org/wiki/Web_Services)

-   License: LGPLv2.1+

### Contact Information

Current Maintainer of libmygpo-qt is **Stefan Derkits**

If you need any help or Information about libmygpo-qt write to the [Mailing List](mailing-list.md)

### Links

-   [Doxygen Documentation](http://stefan.derkits.at/libmygpo-doc/)
-   [Bugtracker for libmygpo-qt](https://bugs.gpodder.org/)
-   [GIT Repo](https://github.com/gpodder/libmygpo-qt)

### Build Dependencies

-   CMake 3.5
-   \+ all dependencies listed below

### Dependencies

-   Qt &gt;= 5.15

### Qt6 support

libmygpo-qt version 1.2.0 supports also building the library with Qt6. The API is the same as in the Qt5 library. To build the library with Qt6 add "-DBUILD\_WITH\_QT6=ON" to your CMake command line. Please note that Qt6 support is still experimental. If you find anything to not work with Qt6, please report a bug.

### Used for

-   [Amarok](http://amarok.kde.org)
-   [Clementine](http://www.clementine-player.org/)

Current Version
---------------

-   Version: 1.2.0

Tarball: <https://stefan.derkits.at/files/libmygpo-qt/libmygpo-qt.1.2.0.tar.gz>
sha256sum: 50ce7f65f402fb3ca509531ddd215a2dd2231fe03fca6b056ffb36f732a5eae6
