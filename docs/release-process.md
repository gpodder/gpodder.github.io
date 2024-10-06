---
title: Release Process
---

This page lists all tasks that have to be done for a gPodder release.

Automating this is discussed in [#293](https://github.com/gpodder/gpodder/issues/293).

Notify Translators
-------------------

`make messages` on the master branch and commit changes, then notify translators via the
[#518](https://github.com/gpodder/gpodder/issues/518) github issue.

Update dependencies
-------------------

If dependencies have been changed or updated, it's a good time to update them:
 - macOS: to update native libraries, see the [gpodder/gpodder-osx-bundle](https://github.com/gpodder/gpodder-osx-bundle) repository;
   once the macOS deps are built and released, update [.github/workflows/release-from-macos.yml](https://github.com/gpodder/gpodder/blob/master/.github/workflows/release-from-macos.yml);
 - macOS bundle python deps: see the `tools/mac-osx/release_on_mac.sh` for the python deps with versions in `pip install` commands;
   update them;
 - Windows: see the `_base.sh` file in the `tools/win_installer` subdirectory of the [gPodder](https://github.com/gpodder/gpodder) repository.
   The files in this directory were adapted from the `dev-utils/win_installer/` subdirectory of the [QuodLibet](https://github.com/quodlibet/quodlibet) repository,
   and upstream may contain fixes or improvements.
 - Python (and flatpak): Update the dependencies in `tools/requirements.txt`

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

- Update `src/gpodder/\_\_init\_\_.py` with new version number and release date, update translations and manpages
  in a single command:
    ```
    make revbump VERSION=x.y.z
    ```
- Add release to `share/metainfo/org.gpodder.gpodder.appdata.xml`, including the notable changes from release notes.
- Commit changes
    ```
    git commit -m "prepare x.y.z release"
    ```

Release notes/website work
--------------------------

- Tag the release
    ```
    git tag -a -m "gPodder x.y.z release" x.y.z
    git push --follow-tags
    ```
- Let the CI take care of building and testing:
  - [Github](https://github.com/gpodder/gpodder/actions/workflows/linttest.yml) testing,
  - [Github](https://github.com/gpodder/gpodder/actions/workflows/release-from-macos.yml) macOS build,
  - [Appveyor](https://ci.appveyor.com/project/elelay/gpodder) Windows build;

- Use the [tools/github_release.py](https://github.com/gpodder/gpodder/blob/master/tools/github_release.py)
  script to download built windows and macOS packages and then upload and prepare the release notes
  (editing while the upload is in progress).
    ```
    cd tools
    GITHUB_TOKEN=xxx python github_release.py --download --mac-github-workflow LATEST_MAC_GA_WORKFLOW --appveyor APPVEYOR_JOB x.y.z
    ```
- Once all is uploaded and release notes are ready, change the tag name and publish the release
- Copy release notes from github releases and post to the Mailing list
- Update versions on the [website](https://github.com/gpodder/gpodder.github.io/tree/master/_data)

Debian package
--------------

- Notify Debian packager that a new release is available: tony on mancill dot com

Flathub package
---------------

The flatpak build files for flathub are in https://github.com/flathub/org.gpodder.gpodder

 - Update gpodder sources URL and sha256sum in the `org.gpodder.gpodder.json` build manifest
 - Add the release under the `<releases>` tag in `appdata.xml`
 - If python dependencies have changed, update `python3-requirements.json` by running
   `flatpak-pip-generator -r <path to tools/requirements.txt in gpodder sources>`
   (see [flatpak-builder-tools](https://github.com/flatpak/flatpak-builder-tools))
 - Make a test build by running `flatpak-builder --user --install build-dir org.gpodder.gpodder.json`
 - Merge your changes to the flathub repo

Ubuntu PPA package
------------------

See https://github.com/gpodder/ppa-scripts
