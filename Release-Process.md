This page lists all tasks that have to be done for a gPodder release.

Testing and release management in the repository
------------------------------------------------

All tests carried out here should be following the Functional tests instructions.

* Test if gPodder works for normal and first-time use cases:
    ```
    \# ... test if basic usage works with current data ...
    mv ~/gPodder ~/gPodder.saved
    \# ... test gPodder (subscribing + downloading) ...
    rm -rf ~/gPodder
    mv ~/gPodder.saved ~/gPodder
    ```
- Update **src/gpodder/\_\_init\_\_.py** with new version number, release date and *release name*
- Update **share/gpodder/credits.txt**.  Use the following command to get the relevant names you may need to add from Git history.  Replace `x.y.z` with the previous gPodder release version (ex. `3.9.3`).
  ```
  git log gpodder-x.y.z.. | git shortlog | grep -v '^[ ]' | sort -u | sed -e 's/\(.*\) ([^)]*):/\1/g'
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

Debian package
--------------

- Notify Debian packager that a new release is available: tony on mancill dot com