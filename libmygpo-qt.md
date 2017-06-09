General
-------

### General Information

libmygpo-qt is a Qt/C++ library wrapping the [gpodder.net Webservice](Web_Services "wikilink"). It is currently used in Amarok & Clementine to retrieve a directory of podcasts & to synchronize podcast subscriptions with [gpodder.net](Web_Services "wikilink")

-   License: LGPLv2.1+

### Contact Information

Current Maintainer of libmygpo-qt is **Stefan Derkits** (HorusHorrendus @ \#gpodder)

If you need any help or Information about libmygpo-qt write to the [Mailing List](Mailing_List "wikilink")

### Links

-   [Doxygen Documentation](http://stefan.derkits.at/libmygpo-doc/)
-   [Bugtracker for libmygpo-qt](https://bugs.gpodder.org/)
-   [GIT Repo](https://github.com/gpodder/libmygpo-qt)

### Build Dependencies

-   CMake 2.6.2
-   \+ all dependencies listed below

### Dependencies

-   Qt &gt;= 4.6
-   [QJson](http://qjson.sourceforge.net/)

### Qt5 support

libmygpo-qt version 1.0.8 supports also building the library with Qt5. The API is the same as in the Qt4 library. To build the library with Qt5 add "-DBUILD\_WITH\_QT4=OFF" to your CMake command line. Please note that Qt5 support is still experimental. If you find anything to not work with Qt5, please report a bug.

### Used for

-   [Amarok](http://amarok.kde.org)
-   [Clementine](http://www.clementine-player.org/)

Current Version
---------------

-   Version: 1.0.8

Tarball: <http://stefan.derkits.at/files/libmygpo-qt/libmygpo-qt.1.0.8.tar.gz>
sha256sum: 83716ea5cd6c0010d4531dd2b0c4e83c12d67b738da6aa15c932fc5901902e81
md5sum: cb67c86919171d6d2356dfb59c3b9571

Future
------

Just some quick Ideas what could be done better with libmygpo-qt 2.0 ;)

-   Code Reusabillity (e.g. Slots error, parse(QByteArray) & parseData are the same in many classes)
    -   possible in v1.X? Only Private Classes need to be changed to use a "ParsableResult" as Parent ...
-   Investigate if it is possible to return QString instead of QNetworkReply\* for Data that will not be parsed (OPML, TXT, XML)
-   Merge Functions that return unparsed data in different formats to a function with an enum parameter for the format
-   Memory vs. RunTime in Objects (e.g. DeviceSyncResult): Save Lists & Co only as QVariant (needed for Properties) and parse on demand or save parsed & QVariant (still possible in v1.X)