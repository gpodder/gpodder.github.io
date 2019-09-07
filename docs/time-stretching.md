---
title: Time stretching (making playback slower or faster)
---

Making playback slower or faster is generally called [time stretching](http://en.wikipedia.org/wiki/Audio_timescale-pitch_modification). There are certain algorithms that maintain the original pitch so that you're favorite podcast speaker doesn't sound like donald duck after being processed. It is a great time saver to listen to podcasts with a faster playback speed. You easily listen to most speakers with 45% speed up and after you're used to it, even 70% speed up is understandable.

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
