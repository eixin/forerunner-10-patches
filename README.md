forerunner-10-patches
=====================

Garmin Forerunner 10 firmware patches (allowing to view elevation, heading, etc)

These patches can be applied to 2.40 firmware only.

The following patches are supported (incremental):
* p1.patch: Virtual Pacer pace range can be set up to 14:00/km (default is 9:00/km). Run/Walk has 5 seconds increments (default is 30 seconds).
* p12.patch: p1 + In running mode the light will NOT be turned on upon each pause/lap (but can be turned on by a button, of course)
* p123.patch: p12 + '4' digit (only large one) looks better (like it is in regular Arial font).
* p1234.patch: p123 + Altitude of the starting point can be seen in paused mode under Speed, when Distance, Time, Speed and Calories are rolling.
* p12345.patch: p1234 + Heading (degrees 0-360) is shown instead of Calories in running mode. You can still see total calories on Totals screen in Run History, but unfortunately without 'cal' text.

Installation:
-------------

1. Take firmware at http://gawisp.com/perry/forerunner/Forerunner10_240.rgn
2. Apply a patch from the list above using 'bspatch' ( http://www.daemonology.net/bsdiff/, Windows version here: http://sites.inka.de/tesla/download/bsdiff4.3-win32.zip ). Like this: 'bspatch Forerunner10_240.rgn Forerunner10_240_p1.rgn p1.patch'.
3. Take RGN_Tool at http://turboccc.wikispaces.com/RGN_Tool (Windows only).
4. Open the output from pt 2. (e.g. Forerunner10_240_p1.rgn) with RGN_Tool and extract the only bin file in it into H:\Garmin\gupdate.rgn, where H: is the letter of flash drive assigned to the FR 10 upon connecting it to the computer. On non-Windows systems you may extract everything starting from offset 0x3C until the end of the patched firmware file (there should be 129084 bytes).
5. Detach the watch and wait until software will be updated.


Notes:
------

1. Everything is provided 'AS IS' and author is not responsible for any possible damage made to the unit.
2. Each incremental patch shows firmware version in Settings/About as 2.41, 2.42 .. 2.45 (like an extra check)
3. You can avoid incrementality of the patches and apply only things you want by finding a difference between patched files and patching a firmware with that difference only. But you should update a kind of checksum (a byte) at the end of firmware file, so that the sum of all bytes starting from 0x78 and until the end of file is a multiple of 0x100. I am using WinHex which calculates a sum of all bytes using its Analyze Block feature.
