This page lists all tasks that have to be done for a gPodder release.

Testing and release management in the repository
------------------------------------------------

All tests carried out here should be following the Functional tests instructions.

* Run `make messages` and then do German translation
* Test if gPodder works for normal and first-time use cases:
    ```
    \# ... test if basic usage works with current data ...
    mv ~/gPodder ~/gPodder.saved
    \# ... test gPodder (subscribing + downloading) ...
    rm -rf ~/gPodder
    mv ~/gPodder.saved ~/gPodder
    ```
- Update **src/gpodder/__init__.py** with new version number, release date and *release name*
- Update **share/gpodder/credits.txt** from the Git history:
  ```
  git log gpodder-`*`x.y.(z-1)`*`.. | git shortlog | grep -v '^[ ]' | sort -u | sed -e 's/`\(.*\)` ([^)]*):/\1/g'`
  ```
- Update translations and manpage:
  ```
  make messages
  make manpage
  ```
- Make sure manpages have the correct version in their headings:
  ```
  man share/man/man1/gpodder.1
  man share/man/man1/gpo.1
  ```

Release notes/website work
--------------------------

- Build the source tarball and release packages
- Upload to <http://gpodder.org/src/> and <http://gpodder.org/releases/>
- Write a post on <http://blog.gpodder.org/>
- Copy release notes from website and post to the Mailing list
- Update bugtracker metadata
  - [Add new version](https://bugs.gpodder.org/editversions.cgi?product=gPodder)

Debian package
--------------

- Notify Debian packager that a new release is available: tony on mancill dot com