Requirements
------------

gPodder may require you to jailbreak your iPod. This is due to restrictions set by Apple. To find out how to do this, click [here](https://help.ubuntu.com/community/PortableDevices/iPhone). Additionally, you're gonna have to install libgpod v0.6.0 or newer.

How-To
------

1.  Jailbreak your iPod touch (tested with iPod touch 1G and Firmware 3.1.3)
2.  Open Cydia and install OpenSSH and MobileTerminal (see the "OpenSSH Access How-To" and "Root Password How-To" sections there)
3.  Change your root password (e.g. by logging in as "root" with password "alpine" via SSH and using "passwd" to change the root pw)
4.  Install [`ipod-convenience`](https://launchpad.net/ipod-convenience) from the Ubuntu repositories (you can also manually mount your iPod via SSHFS)
5.  See also: [iPhone help for Ubuntu](https://help.ubuntu.com/community/PortableDevices/iPhone)
6.  Mount your iPod via sshfs or GVFS (Ctrl+L in Nautilus, then [`ssh://root@ipod/var/mobile/Media/`](ssh://root@ipod/var/mobile/Media/))
7.  Sync to the mountpoint via gPodder (with the "ipod" sync method)

Alternate How-To
----------------

Users of Ubuntu &gt;= 10.04 may be able to avoid jailbreaking their iPods by following the instructions [here](https://help.ubuntu.com/community/PortableDevices/iPhone#Syncing%20with%20GTKpod) for syncing with GTKpod and using `/mnt/ipod`.

Status
------

### What's currently supported

-   Transferring podcasts to your player
-   Podcast artwork

### What's not working quite right yet

-   [Enhanced podcasts](http://en.wikipedia.org/wiki/Enhanced%20podcast) can be played, but without the extra features.
-   Video podcasts don't show up in the video menu. If you try to play them from the Music &gt; Podcasts menu, you only get to hear the audio.
-   Some podcasts get reverted to their original 'not played' status when their play count is set to 0. This is part of a bigger issue where the iPod touch doesn't maintain play counts correctly. Unfortunately, we don't have enough information about this at the moment. [Libgpod Sourceforge bug](https://sourceforge.net/tracker/index.php?func=detail&aid=1895418&group_id=67873&atid=519273)

FAQ
---

**Q:** My new podcasts don't show up in the podcast menu!

**A:** Unmount your iPod before you go look for them. If you have installed ipod-convenience, just do 'iphone-umount' or 'ipod-touch-umount' in a terminal.
