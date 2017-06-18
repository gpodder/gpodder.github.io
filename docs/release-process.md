---
title: Release Process
---

This page lists all tasks that have to be done for a gPodder release.

Automating this is discussed in https://github.com/gpodder/gpodder/issues/293

Testing and release management in the repository
------------------------------------------------

* Test if gPodder works for normal and first-time use cases (TODO this should be done in CI):
    ```
    \# ... test if basic usage works with current data ...
    mv ~/gPodder ~/gPodder.saved
    \# ... test gPodder (subscribing + downloading) ...
    rm -rf ~/gPodder
    mv ~/gPodder.saved ~/gPodder
    ```
- Update **src/gpodder/\_\_init\_\_.py** with new version number, release date and *release name*

- Update translations and manpage:
  ```
  make messages
  make manpage
  ```
- Make sure manpages have the correct version in their headings (TODO: move this to CI):
  ```
  man share/man/man1/gpodder.1
  man share/man/man1/gpo.1
  ```

Release notes/website work
--------------------------

- Tag the release
- Let the CI take care of building + uploading to Github releases (TODO)
- Write a post on <http://blog.gpodder.org/>
- Copy release notes from website and post to the Mailing list

Debian package
--------------

- Notify Debian packager that a new release is available: tony on mancill dot com