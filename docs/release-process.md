---
title: Release Process
---

This page lists all tasks that have to be done for a gPodder release.

Automating this is discussed in [#293](https://github.com/gpodder/gpodder/issues/293).

Notify Translators
-------------------

`make messages` on the master branch and commit changes, then notify translators via the
[#518](https://github.com/gpodder/gpodder/issues/518) github issue.

Update Windows and macOS dependencies
---------------------------------

Not required, but it's a good time to update dependencies:
 - macOS: see the [gpodder/gpodder-osx-bundle](https://github.com/gpodder/gpodder-osx-bundle) repository;
   once the macOS deps are built and released, update [.circleci/config.yml](https://github.com/gpodder/gpodder/blob/master/.circleci/config.yml);
 - Windows: see the `tools/win_installer` subdirectory of the [gPodder](https://github.com/gpodder/gpodder) repository.

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

- Test latest Windows and macOS builds in a similar manner.

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
    git tag -a -m "gPodder x.y.z release" x.y.z
    git push --follow-tags
    ```
- Let the CI take care of building and testing:
  - [Travis](https://travis-ci.org/gpodder/gpodder/builds) testing,
  - [CircleCI](https://circleci.com/gh/gpodder/workflows/gpodder) macOS build,
  - [Appveyor](https://ci.appveyor.com/project/elelay/gpodder) Windows build;

- Use the [tools/github_release.py](https://github.com/gpodder/gpodder/blob/master/tools/github_release.py)
  script to download built windows and macOS packages and test one last time...
- Use the [tools/github_release.py](https://github.com/gpodder/gpodder/blob/master/tools/github_release.py)
  script to upload and prepare the release notes (editing while the upload is in progress).
- Once all is uploaded and release notes are ready, change the tag name and publish the release
- Copy release notes from github releases and post to the Mailing list
- Update versions on the [website](https://github.com/gpodder/gpodder.github.io/tree/master/_data)

Debian package
--------------

- Notify Debian packager that a new release is available: tony on mancill dot com
