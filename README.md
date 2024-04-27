# dejavuln-autoroot

This is a tool to root LG TVs and automatically install
[Homebrew Channel](https://github.com/webosbrew/webos-homebrew-channel).
It uses [DejaVuln](https://twitter.com/jcxdev/status/1781668313958945132),
which works on webOS 3.5 and newer.

## Patch status

> [!WARNING]
> LG has already started testing patched firmware. Do not update your
> firmware if you want to be able to root your TV.

While it has not yet been released, LG is testing patched firmware for several
2023 OTAIDs (W23O, W23H, and W23P: all 2023 OLEDs and more). It is likely that
DejaVuln will be patched in any firmware with a webOS version of 8.4.x
(codename number1-namtok).

I expect to see patched firmware for most webOS 4.5+ OTAIDs start rolling out
relatively soon. However, webOS 3.5 will almost certainly never receive
patched firmware, and 4.0 probably won't either.

Right now, unless you messed with the "NSU Mode" setting in the Instart menu
(which is not recommended), you will not have patched firmware.

## Instructions

1. Download the latest release (*not* the files named "Source code") from the
   [Releases](https://github.com/throwaway96/dejavuln-autoroot/releases)
   page.
   ![Releases](https://github.com/mariotaku/dejavuln-autoroot/assets/830358/0f6ab7b8-a0cf-47e5-8741-88296f934e0b)
2. Extract the archive to the root directory of a USB drive. (It should be
   formatted with FAT32 or NTFS and only have one partition, and placed
   like screenshot below.)
   ![Correct file placement](https://github.com/mariotaku/dejavuln-autoroot/assets/830358/b066c827-2d84-425f-bcef-943ee8a19545)
3. Plug the USB drive into your TV. (Make sure it's the only USB drive
   connected.)
4. Open the USB drive in the Music app and browse to
   `lol$(sh$IFS$(find$IFS/tmp`.
5. Try to play the MP3 file
   (`usb$IFS-maxdepth${IFS}3$IFS-name${IFS}autoroot.sh)).mp3`).
6. After the pop-up messages tell you rooting is complete, eject the USB
   drive.

If you have the LG Developer Mode app installed, you *must* remove it before
rebooting. **Do not** install it while your TV is rooted.

## Settings

You can influence the behavior of the script by creating certain files in the
root directory of the USB drive:

* `autoroot.debug` - Enables additional logging.
* `autoroot.telnet` - Makes a root shell available via telnet on port 23 when
  the script starts.

## Troubleshooting

If the script fails, you must delete `autoroot.once` from the USB drive and/or
reboot the TV before it will run again.

A log file named `autoroot.log` should be created on the USB drive.

On webOS 8 (webOS 23), you may have to try multiple times; it seems that
restarting `appinstalld` does not reliably make it detect the existence of
`devmode_enabled`. May also apply to webOS 7.

Toasts from the script may be hidden by system messages (like the one about
the MP3 file not being recognized).

If the toast and/or log says "Rooting complete" but you don't see Homebrew
Channel, reboot the TV. Make sure Quick Start+ is disabled.

Make sure the archive is extracted such that `autoroot.sh` is in the root
directory of the USB drive.

## Support

You can find more information at [webosbrew.org](https://www.webosbrew.org/).

If you need help rooting your TV, try the
[OpenLGTV Discord](https://discord.gg/hXMHAgJC5R). Before you ask a question,
check the FAQ (#faq) to see if it is answered there! Attach your `autoroot.log`
when asking for help.

## Credits

* DejaVuln was discovered by [Jacob Clayden](https://jacobcx.dev/).
* The very similar CVE-2023-6319 was discovered by
  [Bitdefender](https://www.bitdefender.com/blog/labs/vulnerabilities-identified-in-lg-webos/).

## License

This program is free software: you can redistribute it and/or modify it under
the terms of the GNU Affero General Public License as published by the Free
Software Foundation, either version 3 of the License, or (at your option) any
later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY
WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE. See the GNU Affero General Public License for more details.

You should have received a copy of the GNU Affero General Public License along
with this program. If not, see <https://www.gnu.org/licenses/>.

See `COPYING` for details.
