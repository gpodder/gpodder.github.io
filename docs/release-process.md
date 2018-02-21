---
title: Release Process
---

This page lists all tasks that have to be done for a gPodder release.

Automating this is discussed in [#293](https://github.com/gpodder/gpodder/issues/293).

Testing and release management in the repository
------------------------------------------------

- Test if gPodder works for normal and first-time use cases (TODO this should be done in CI):
    ```
    \# ... test if basic usage works with current data ...
    mv ~/gPodder ~/gPodder.saved
    \# ... test gPodder (subscribing + downloading) ...
    rm -rf ~/gPodder
    mv ~/gPodder.saved ~/gPodder
    ```
- Update **src/gpodder/\_\_init\_\_.py** with new version number and release date, update translations and manpages
  in a single command:
    ```
    make revbump VERSION=x.y.z
    ```
- Commit changes

Release notes/website work
--------------------------

- Tag the release
    ```
    git tag -a x.y.z -m "gPodder x.y.z release
    git push --follow-tags
    ```
- Let the CI take care of building and testing (+ uploading to Github releases -- TODO)
- Create a release draft in [github](https://github.com/gpodder/gpodder/tags).
  [Comparing](https://github.com/gpodder/gpodder/compare/3.10.0...3.10.1)
  with previous release might be handy
- Check [Travis](https://travis-ci.org/gpodder/gpodder/builds)
  and [CircleCI](https://circleci.com/gh/gpodder/workflows/gpodder).
- Write a post on <http://blog.gpodder.org/>
- Copy release notes from website and post to the Mailing list

Debian package
--------------

- Notify Debian packager that a new release is available: tony on mancill dot com

macOS package
------------

- download macOS package and checksums from [CircleCI](https://circleci.com/gh/gpodder/workflows/gpodder)
  and test it (same as **Testing and release management in the repository**).
- attach macOS package and checksums to the release.
