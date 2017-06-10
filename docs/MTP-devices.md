MTP (Media Transfer Protocol) supports the transfer of music files on digital audio players and movie files on portable media players

-   MTP info on Wikipedia: <http://en.wikipedia.org/wiki/Media_Transfer_Protocol>
-   MTP specification: <http://www.usb.org/developers/devclass_docs/MTP_1.0.zip>

### Dependencies

-   [libmtp](http://libmtp.sourceforge.net/index.php?page=download) (Debian/Ubuntu: sudo aptitude install libmtp7 mtp-tools)
-   [pymtp](http://nick125.com/projects/pymtp) (Debian: sudo aptitude install python-pymtp)
-   Compatible MTP device, see <http://libmtp.sourceforge.net/index.php?page=compatibility>

### Helpful commands

-   The command `lsusb`. You should see a line corresponding to your device.
-   The command `mtp-detect` should dump a huge amount of information about your device.
-   The command `mtp-tracks` should list all tracks present on your device.

### Enabling MTP support in gPodder

-   Go to Preferences, open the "Player" tab and choose "mtp-based device"

### Troubleshooting

-   first, verify that you have libtmp and pymtp working
-   run from a shell `gPodder` `--verbose`
-   send a bug to gPodder including a description on what has happened and the result of the previous command

MTP support has mostly been written by Jérôme Chabod.
