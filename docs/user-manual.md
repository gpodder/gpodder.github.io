---
title: The gPodder User Manual
---

In general, the assumption is that you are running the latest version of **gPodder 3**. Things written here might not exist or work as described in older versions of gPodder. When information applies to older versions of gPodder, this will (should) be explicitly stated.

* TOC
{:toc}

---

Installation
------------

If you want to try the latest version, see the instructions at: [Run from Git](run-from-git.md)

In general, if you get gPodder via Git or the source tarball, simply run it directly from the source checkout and don't try to install it system-wide (use your distro's packages for system-wide installation).

gPodder is designed to also run directly from a source checkout (the maintainer uses it like that all the time):

-   Use **bin/gpodder** to run the GUI
-   Use **bin/gpo** to run the CLI

If you have checked out the source, but are missing dependencies, you can make the source checkout a self-contained gPodder setup with all dependencies by running:

-   **python3 tools/localdepends.py**

This will download feedparser and mygpoclient and place them into **src/** - **bin/gpodder** and **bin/gpo** will be able to pick these modules up from there, so all you really need is Python &gt;= 3.5 on your system.

Configuration
-------------

gPodder has numerous configuration options to set its behaviour: how it plays podcasts, handles downloads, and many others.

To change gPodder's configuration, open the Preferences dialog box by choosing **Podcasts &gt; Preferences** from the menu bar, clicking the Preferences button on the toolbar, or typing `Ctrl-P`. Then click the tab containing the options you want to change.

### General Preferences

Click the **General** tab to see gPodder's general configuration options.

**Audio player:** Use this drop-down list of compatible audio players installed on your system to choose the one gPodder uses to play audio podcasts. Currently pre-populated application lists are only supported in Linux. (OS X and Windows users, keep reading!)

You can also click the Edit button next to the list to enter a custom audio player command. For example, you might want to run the player with some additional options, or choose a different player that does not appear on the list.

**Video player:** Use this drop-down list to choose the video player gPodder uses to play video podcasts. This option works the same as the *Audio player* option, except that it shows media players capable of playing video files.

### gpodder.net Preferences

[gPodder.net](http://www.gpodder.net/) is a Web service that helps you synchronize your podcast subscriptions across multiple devices, discover interesting new podcasts and recommend your podcasts to others. Click the **gpodder.net** tab to set how gPodder interacts with gPodder.net.

  
**Note:** To use gPodder.net, you need to [register for a user account](http://www.gpodder.net/register/) first.

**Synchronize subscriptions and episode actions:** Check this box to merge the subscriptions on your computer or device with your subscription list on gPodder.net. These podcast subscriptions are now available to any other devices you sync with gPodder.net.

**Username:** Enter your gPodder.net username.

**Password:** Enter your gPodder.net password.

**Device name:** Enter a meaningful name for your computer, or keep the one gPodder.net assigns. Make sure the name is unique.

**Replace list on server with local subscriptions:** Click this button to replace the subscription list on gPodder.net with the list on your device.

  
**Caution:** Any podcast subscriptions on gPodder.net but not on your local computer will be lost.

### Updating Preferences

Click the **Updating** tab to see gPodder's options for updating feeds and downloading new episodes.

**Update interval:** Drag this slider to choose the frequency that gPodder checks your feeds for new podcast episodes. This time period can be between 10 minutes and 12 hours. If you drag the slider all the way to the left, gPodder will not check for new podcasts automatically, and you will have to update them yourself.

**Maximum number of episodes per podcast:** Use this spin box to set the maximum number of episodes that gPodder keeps in each podcast feed. Once this maximum is reached, gPodder deletes the oldest episodes in the feed as new ones are added.

**When new episodes are found:** Use this drop-down list to choose what you want gPodder to do when it finds new podcast episodes on a feed. The available options are:

-   *Do nothing* - gPodder marks new episodes in the feeds as new, but takes no other action.
-   *Show episode list* - gPodder displays a window showing a list of all new episodes available for download. You can then choose the specific episodes that you want to download, ignore, or mark as old.
-   *Add to download list* - gPodder automatically adds all new episodes to the the download list under the **Downloads** tab in the main window. However, they are marked as paused, and you need to right-click on them and choose **Download** to get them.
-   *Download immediately* - gPodder adds new episodes to the download queue and automatically downloads them.

### Clean-up Preferences

Click the **Clean-up** tab to see gPodder's options for managing old downloaded podcasts.

**Delete played episodes:** Drag this slider to set the length of time before gPodder automatically deletes old podcasts. This time period can be between one and 30 days. If you drag the slider all the way to the left, podcast episodes will not be deleted automatically, and you will have to manage them yourself.

**Remove played episodes even if unfinished:** By default, gPodder automatically deletes old played but unfinished episodes. Clear this check box if you would like to keep unfinished episodes until you have played them completely. If you have chosen to delete played episodes manually, this option is not available.

**Also remove unplayed episodes:** By default, gPodder automatically deletes played episodes but leaves unplayed ones alone. Check this box if you want gPodder to clean up unplayed episodes as well. If you have chosen to delete played episodes manually, this option is not available.

### Devices Preferences

Click the **Devices** tab to see gPodder's options for portable media player devices.

**Device type:** Choose the type of device from this drop-down list that matches your player. The available options are:

-   *Filesystem-based* - Choose this device if your media player is treated like a simple USB storage device, and media files are added by copying them to a directory on the device.

Note that as of version 3.2.0, gPodder only supports syncing with filesystem-based devices. Check the user documentation for your device if you're unsure what kind it is.

**Mountpoint:** Click this button to choose the mount point where your media player normally appears on your system. For example, on a Windows system it might be drive `F:`.

**Create Playlists on device:** Enable this option to have gPodder create a m3u format playlist on your device during the sychronisation process. This is only supported for filesystem-based media players. If 'Create Playlists on device' is enabled, the following settings can also be configured:

-   *Playlists Folder* - Click this button to choose the folder on your media player in which your playlist files will be created.
-   *Remove episodes deleted on device from gPodder* - If this option is selected, gPodder will offer to delete episodes deleted on the device since the last sync from the gPodder itself.

**After syncing an episode:** Choose what you want gPodder to do after it transfers a podcast eposide to your player. The available options are:

-   *Do nothing* - gPodder simply transfers the file and takes no further action.
-   *Mark as played* - gPodder transfers the file and marks it as already played.
-   *Delete it from gPodder* - gPodder transfers the file, then deletes it from the computer.

**Only sync unplayed episodes:** Check this box if you want gPodder to ignore episodes that have already been played, when synchronizing podcasts to your device.

### Flattr options

[Flattr](http://flattr.com/) is a microdonation system that allows you to fund online content creators. You pay a small monthly fee (set by yourself), and it is shared between all the online resources you "flattr," or choose to support. Click the **Flattr** tab to see gPodder's options for Flattr.

### Advanced configuration options

gPodder has many configuration options that are not all directly accessible through the Preferences dialogue box. Click the **Edit config** button to access the gPodder Configuration Editor, where you can see and change the full list of configuration options.
For an up-to-date list, possible values and the defaults, please see [src/gpodder/config.py](https://github.com/gpodder/gpodder/blob/master/src/gpodder/config.py).

Everyday usage
--------------

### Adding a Podcast

Manually add one at a time using Menu - Subscriptions -&gt; Subscribe to new podcast and paste in the URL of the RSS feed.

#### Shortcuts for URLs

gPodder tries to be smart about what you enter in the URL field when adding podcasts to save you some typing:

-   You can leave out the leading `http://`, as gPodder will automatically add it if the URL does not contain a URL scheme.

<!-- -->

-   If the website has a correct `<link>` tag to the podcast RSS feed, gPodder can (most of the time) autodiscover the feed. So, instead of entering "**feeds.feedburner.com/uncontrolledairspace**", you can enter "**www.uncontrolledairspace.com**", and gPodder will figure out the feed URL (but see the next hint for another nice shortcut for FeedBurner URLs)

<!-- -->

-   gPodder supports the "fb:" prefix for FeedBurner URLs, so that instead of having to type "**feeds2.feedburner.com/podcastname**", you can type "**fb:podcastname**", and gPodder will be smart enough to expand the URL correctly.

<!-- -->

-   Another prefix that works is "yt:" for YouTube users. Use **yt:username** to add videos from YouTube user "username" to gPodder. Please note that you need a google account to subscribe YouTube user channels: you can find the instructions [here](youtube.md).

<!-- -->

-   For Soundcloud feeds, you can use the "sc:" prefix to add SoundCloud users. Use **sc:crunchtime** to add music published by user "crunchtime" on Soundcloud.

<!-- -->

-   If you know about other services where this makes sense, please get in touch, and we can add even more prefixes.

#### Backing up the subscription list

The Podcasts menu provides an easy way to save your subscription list to an **OPML file**. The OPML file contains URLs for all the feeds you are subscribed to. It does *not* contain the status of episodes. You can re-import OPML files using the Podcasts menu. The [OPML file format](http://www.opml.org/) is a simple XML format that can be used to move feed subscriptions between different RSS-aware applications.

You can also backup the files **Database** (an SQLite 3 database containing subscription and episode information) and **Settings.json** (a JSON file containing your settings) in **$GPODDER\_HOME** (defaults to ~/gPodder/).

#### Importing subscriptions from iTunes

Export your iTunes podcast subscriptions to an OPML file. Copy it over to your device or computer and load it into gPodder with the **Import from OPML file** menu item. To export your iTunes podcast subscriptions to an OPML file right click on "podcasts" in your source menu on the right hand side. Select "export" and save as an OPML file. See <http://www.apple.com/itunes/podcasts/>.

#### Importing subscriptions from an OPML file

Older versions of gpodder have an **Import from OPML file** menu item while newer versions may not. If you have the import option, you can select it, browse to your opml file and import it.

1.  Launch gpodder
2.  Select **Choose from a list of example podcasts** on the gpodder startup assistant
3.  Change the **OPML/Search** field to the file url for your opml file (e.g., <file:///home/username/my.opml>''')
    -   You can open the opml file with your browser's "open file" to obtain the <file://> url if you are unsure of it.

4.  Select All podcasts and Add

At this point you should have a local list of subscriptions. You can push these up to gpodder.net via the **Replace list on server with local subscriptions** button on the Preferences : gpodder.net tab.

### Listening to downloaded episodes

Most of the audio player applications available for the N8x0 do not support bookmarking (so you can resume playing a podcast from a saved point). [Panucci](http://panucci.garage.maemo.org/) is a resuming audiobook and podcast player written by the gPodder people that is available from Maemo Extras. Install the package and set the **player** variable to **panucci** (don't forget to set **maemo\_allow\_custom\_player**, as stated above).

#### Appending episodes to the current playlist

Most applications will stop the current song/episode and start playing the selected episodes when clicking on **Play**. You can avoid that by setting a custom command in the settings dialog:

<table>
<thead>
<tr class="header">
<th><p>Application</p></th>
<th><p>Command</p></th>
<th><p>Remarks</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Aqualung</p></td>
<td><p><code>aqualung</code> <code>-N0</code> <code>-E</code></p></td>
<td><p>This option loads the files, but does not start playback automatically, you can try adding the -L command for that, but that tends to start playback on the last one loaded. But once the first file is playing, you can load up your play-list from gPodder for hours of listening enjoyment.</p></td>
</tr>
<tr class="even">
<td><p>VLC 0.9.4</p></td>
<td><p><code>vlc --playlist-enqueue --started-from-file</code> (Linux)<br />
<code>&quot;C:\Program Files\VideoLAN\VLC\vlc.exe&quot; --playlist-enqueue --started-from-file</code> (Windows)<br />
<code>/Applications/VLC.app/Contents/MacOS/VLC</code> (Mac)</p></td>
<td><p>This will queue up the file and play the first one and you can add more while you're listening. You may have to click your play button, but once playing it ought to continue to play the created playlist.</p></td>
</tr>
<tr class="odd">
<td><p>SMPlayer</p></td>
<td><p><code>smplayer -add-to-playlist %F</code></p></td>
<td><p>Adds the files to the current SMPlayer playlist</p></td>
</tr>
</tbody>
</table>

### Synchronising podcasts to MP3 players

Synchronising podcasts to MP3 Players is currently only supported for filesystem-based media players. iPod support is planned for a future release.

Before you can synchronise podcasts to your media player, you should ensure that the player has been set up properly in the 'Device' tab. See above for details.

To initiate a sync, select 'Sync to Device' from the 'Extras' menu:

![Initiate a sync](extras-sync.png)

Previous versions of gPodder required you to sync episodes indivdually - now all episodes are synced at once.

If you have the 'Create Playlists on device' option enabled, the m3u playlists will be written to your device and then the episodes will be copied over. You see the current status of the sync from the 'Progress' tab of the main gPodder window. From here, you can also control the number of episodes written to your device concurrently via the 'Limit downlads' setting, which also applies to device synchronisation. However, the 'Limit Rate' setting in the 'Progress' tab has no effect on synchronisation speed.

#### Playlists

If the 'Create playlists on device' option is enabled, gPodder will create playlists on your filesystem-based media player during each sync. One playlist is created per channel. The playlist is created in date order, so that the playlist will always start at the oldest episode and end at the newest. As new episodes are synced to the player, they are automatically added to the playlist. If you delete an episode from within gPodder, it is removed from the playlist.

#### Removing episodes via synchronisation

If you have the 'Create playlists on device' option enabled, you can also enable the option 'Remove episodes deleted on device from gPodder'.

![Removing episodes via synchronisation](gpodder-devices.png)

When this feature is enabled, users can delete episodes from gPodder by deleting them from their media player and then performing a sync with gPodder. gPodder uses the m3u playlist to track what episodes were synchronised to the device.

With this feature enabled, if you deleted episodes from your device and then synchronise again, gPodder will present you with a list of deleted episodes. You can choose which of these episodes you wish to delete - all, none or some. See the example below:

![List of deleted episodes](gpodder-remove-episodes.png)

Any episodes that you choose not to delete will not be deleted on from gPodder, but will not be restored to your player. In order to sync them back to your player, you will then need to disable this feature from Devices Preferences and those episodes will be copied back at the next synch.

If 'Remove episodes deleted on device from gPodder' is not enabled, any episodes deleted from the device will be copied back over during the next sync. You will instead have to manually delete episodes from within gPodder itself.

#### Custom file names

You can use custom file names when synchronising. This makes browsing files on your device much more convenient.

The default value for the custom filename field is {episode.basename}. This will work for most podcasts. However, occasionally you may find a podcast where the producers don't provide unique information in the tags, which can result in multiple episodes being given the same name (e.g. podcast.mp3), and thus overwriting one another on synchronisation. One workaround to this is to include the {episode.sortdate} data. Multiple fields can be concatenated, e.g.: "{episode.sortdate}\_{episode.basename}" which will result in files of the form "2012-01-14\_podcast.mp3".

For podcasts that release multiple episodes on the same day, even this might not be enough. Try also {episode.sortdate}\_{episode.title}, or even {episode.sortdate}\_{episode.published}

Both playlist creation and the ability to remove episodes from gPodder by deleting them from the device will work with custom file names enabled.

### Keeping downloaded episodes (Archiving)

If you wish to keep an episode around you may archive it by right-clicking on the episode and selecting "Archive". The episode must be downloaded for the "Archive" option to show.

Once an episode has been archived, gPodder will do its best to never delete it:

-   If auto-cleaning is enabled, archived episdoes will not be cleaned.
-   When selecting multiple episodes, deleting the selected episodes will (should) keep any archived ones.

Advanced topics
---------------

### Command-line interface

gPodder includes a command-line interface. The command is called `gpo`. You can get a list of possible actions by running the command without any parameters.

### Using a HTTP proxy server

You can use a HTTP proxy server for downloading episodes and feeds. Newer versions of gPodder do not provide a way to do so in the GUI, but respect the environment variable **http\_proxy**. How to set the **http\_proxy** environment variable in different operating systems is described here:

-   [Setting http\_proxy in Windows, Mac OS X and Linux/Unix](http://docs.activestate.com/activeperl/5.10/faq/ActivePerl-faq2.html#setting_http_proxy)

If you want to use a proxy for gPodder, but don't want to use a proxy for other applications, you can create a short shell script:

    #!/bin/sh
    export http_proxy=http://username:password@hostname:port
    gpodder


### Using Yahoo! Pipes to fix feeds

There might be some problems with feeds (see [the related bug report](https://bugs.gpodder.org/show_bug.cgi?id=528)) - to fix it, you can try to use Yahoo Pipes:

1.  Create a new pipe with the problematic feed as source
2.  Make no transformation
3.  Use the RSS output of the resulting pipe in gPodder

See a [screenshot of the pipe source](http://i29.tinypic.com/6gyauu.jpg) to get an idea of how it should look like.

### Reporting download problems

If you have got problems with episode downloads, please follow the instructions on the page about [Reporting download bugs](reporting-download-bugs.md).


### Time stretching (making playback slower or faster)

Making playback slower or faster is generally called [time stretching](http://en.wikipedia.org/wiki/Audio_timescale-pitch_modification). There are certain algorithms that maintain the original pitch so that you're favorite podcast speaker doesn't sound like donald duck after being processed. It is a great time saver to listen to podcasts with a faster playback speed. You easily listen to most speakers with 45% speed up and after your used to it, even 70% speed up is understandable.

The audio files can be processed by gPodder before transferring them to a portable device. The following is a script for speeding up a single mp3 file by 45%:

    #!/bin/bash
    # mp3faster - script for making mp3 playback faster with soundstretch
    #
    # debian/ubuntu package requirements
    # apt-get install soundstretch lame libid3-3.8.3v5
    #
    # rhel/centos/fedora package requirements
    # yum install soundtouch lame id3lib
    #
    # sample usage for converting all mp3 files in a directory structure:
    # find -name "*.mp3" -print0 | xargs -0 -i mp3faster {}
    #
    # (1) decode mp3 to wav file
    # mpg321 --wav "$1.wav" "$1"
    # the above decoding technique doesn't always work, and can sometimes 
    # create a wav file that plays back too fast. Seems to happen with mp3 files that
    # have a low bitrate (< 80kbps). Using the lame alternative below get's around this.
    # alternative #1 to decoding an mp3 to wav
    # lame --decode "$1" "$1.wav"
    # alternative #2 to decoding an mp3 to wav
    # mpg321 -b 10000 -s -r 44100 $1 | sox -t raw -r 44100 -s -w -c2 - "$1.wav"

    # (2) process file with soundstretch
    # soundstretch "$1.wav" "$1.fast.wav" -tempo=+45

    # (3) encode mp3 file
    # lame --preset fast medium "$1.fast.wav" "$1.2.mp3"

    # (1) & (2) & (3) can get a huge performance improvement through using pipelining 
    # because no disk I/O and no temporary wave file is used between input and output
    lame --quiet --decode "$1" - | soundstretch stdin stdout -tempo=+45 | lame --quiet --preset fast medium - "$1.2.mp3"

    # copy id3 tags from old file
    id3cp "$1" "$1.2.mp3"

    # rename original mp3 file to .bak extension
    mv "$1" "$1.bak"
    # rename processed mp3 file to original name
    mv "$1.2.mp3" "$1"

**Time Stretching on Windows**

The following batch file can be used for time stretching on Windows (instead of the above two bash scripts). Note that this batch file deletes the original MP3 file (replacing it with the stretched version), it does not copy any MP3 tags to the new file (so all tags will be lost), and soundstretch and lame must be installed. Name this file speedup.bat and set `cmd_download_complete` to point to this file. In gPodder 2.14, there seems to be a problem with `cmd_download_complete` that causes every other download to fail when using this script. If you run into this problem, consider using the script below instead ("Alternate Time Stretching on Windows").

    REM speedup.bat - script for making mp3 playback faster with soundstretch
    REM soundstretch and lame must be installed first.
    REM deletes the original .mp3 and replaces it with the processed version
    REM does not copy any tags from the original .mp3 to the processed version

    REM exit if it's not an .mp3
    set FILE=%GPODDER_EPISODE_FILENAME%
    if not %FILE:~-3%==mp3 exit

    REM decode mp3 to wav file
    lame --decode "%FILE%" "%FILE%.wav"

    REM process file with soundstretch
    soundstretch "%FILE%.wav" "%FILE%.fast.wav" -tempo=+50 -speech

    REM encode mp3 file
    lame --preset standard "%FILE%.fast.wav" "%FILE%.2.mp3"

    REM clean up - delete original .mp3, replace with processed .mp3
    del "%FILE%"
    del "%FILE%.wav"
    del "%FILE%.fast.wav"
    move "%FILE%.2.mp3" "%FILE%"

**Alternate Time Stretching on Windows**

This alternate time stretching script will time-stretch EVERY .mp3 file in your gPodder downloads folder - so this script is only useful if you listen to (and delete) all the .mp3 files in your downloads folder, before you download more files.

This can be used as a stand-alone program, and in theory it can be used with `cmd_all_downloads_complete` (but in gPodder 2.14, there seems to be a problem with `cmd_all_downloads_complete` that causes this script to get started multiple times). If you have a slower system and you don't want this script to take over the CPU, consider starting the script with priority `/LOW` using the `START` command.

As with the script above, this batch file deletes the original MP3 file (replacing it with the stretched version), it does not copy any MP3 tags to the new file (so all tags will be lost), and soundstretch and lame must be installed first. In the script, replace `C:\gPodder\gpodder-2.14-win32\downloads` with the path to your gPodder downloads folder.

    REM Time-stretches EVERY .mp3 file in your gPodder downloads folder!
    REM Soundstretch and lame must be installed first.
    REM Deletes the original .mp3 and replaces it with the processed version.
    REM Does not copy any tags from the original .mp3 to the processed version.
    REM Replace C:\gPodder\gpodder-2.14-win32\downloads with
    REM   the path to your gPodder downloads folder before running!

    for /R "C:\gPodder\gpodder-2.14-win32\downloads" %%F in (*.mp3) do (

    REM decode mp3 to wav file
    lame --decode "%%F" "%%F.wav"

    REM process file with soundstretch
    soundstretch "%%F.wav" "%%F.fast.wav" -tempo=+50 -speech

    REM encode mp3 file
    lame --preset standard "%%F.fast.wav" "%%F.2.mp3"

    REM clean up (delete original .mp3, replace with processed .mp3) 
    del "%%F"
    del "%%F.wav"
    del "%%F.fast.wav"
    move "%%F.2.mp3" "%%F"

    )

### Changing the downloads folder location and the gPodder Home folder

To change the download directory or gPodder Home, you can set one (or both) of these two environment variables:

-   **`GPODDER_HOME`**: Downloads will be saved in the folder "Downloads" inside the new Home folder you set
-   **`GPODDER_DOWNLOAD_DIR`**: Downloads will be saved directly in the folder you specify (which does not have to be in the gPodder Home folder)

There are various ways of setting these variables, depending on your distro/operating system and on the version of gPodder you are using.

#### Default settings

Here are the default download folder locations:

-   **Linux/FreeBSD/Mac OS X:** ~/gPodder/Downloads/
-   **Windows:** Selected via a dialog on first start (use the start menu item "gPodder (set download folder)" to change it)

If **`$GPODDER_HOME`** is not set, it defaults to `~/gPodder/`. The settings and database files will always be stored in **`$GPODDER_HOME`**.

#### Session-wide changes on Ubuntu Linux

With gPodder 3.3.0 (and also 3.4.0) in Ubuntu (at least 12.10 and 13.04), you can't change the environment variables for gPodder Home and for the download directory through Preferences &gt; Edit config (see [bug 1718](https://bugs.gpodder.org/show_bug.cgi?id=1718)). One thing you can do instead is this:

-   Open a terminal
-   Type: `gedit` `~/.pam_environment`

A text file will open up (it could well be empty). Add one or two of the following lines (depending on whether you want to change both these variables or just one):

-   GPODDER\_HOME=\[path to directory you want to use\] - eg. GPODDER\_HOME=/media/BigDisk/Podcasts/
-   GPODDER\_DOWNLOAD\_DIR=\[path to directory you want to use\]

If you are using Kubuntu, you must do the following :

-   Open a terminal
-   Type : `kate` `~/.kde/env/setgpodder.sh`

An empty text file will open (you can name it whatever you want instead of *setgpodder*,it could be *gpodderdirs*, etc). Add one or two of the following lines (depending on whether you want to change both these variables or just one):

-   GPODDER\_HOME=\[path to directory you want to use\] - eg. GPODDER\_HOME=/media/BigDisk/Podcasts/
-   GPODDER\_DOWNLOAD\_DIR=\[path to directory you want to use\]

Read more on [persistent environment variables in Ubuntu](https://help.ubuntu.com/community/EnvironmentVariables#Persistent_environment_variables).
