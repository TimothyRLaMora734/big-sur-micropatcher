# big-sur-micropatcher
A primitive USB patcher for installing macOS Big Sur on unsupported Macs

Thanks to jackluke and ASentientBot for their hard work to get Big Sur running on unsupported Macs!

This documentation is extremely bare-bones at the moment, but hopefully it's better than nothing. Remember that you *do this at your own risk*, you could easily lose your data, expect bugs and crashes, Big Sur is still under development (as is this patcher), etc.

Quick instructions for use:

1. Obtain a copy of the macOS Big Sur Developer Preview and use `createinstallmedia` as usual to create a bootable USB stick with the installer and recvoery environment, as you would on a supported Mac. (This patcher currently requires that the name of the USB stick remain "Install macOS Beta". Do not rename the USB stick at any point.)
2. Also obtain a copy of ASentientBot's Hax.dylib or Hax2Lib.dylib (the latter is contained inside Hax2.app).
3. Download this micropatcher, then run `micropatcher.sh` to patch the USB stick. (If you are viewing this on GitHub, and you probably are, then click "Clone" then "Download ZIP".)
4. After the patcher finishes, Copy Hax.dylib or Hax2Lib.dylib onto the USB stick. (Or you can do it before running the patcher if you prefer.)
5. Boot from the USB stick.
6. If you need to do any formatting or partitioning with Disk Utility, you can do it now, or between steps 8 and 9, it's up to you.
7. Open Terminal, then run `/Volumes/Image\ Volume/set-vars.sh`. This script will change boot-args and csrutil settings as needed. Don't forget that tab completion is your friend! You can type `/V<tab>/I<tab>/se<tab>` at the command prompt -- that's much less typing! (Run `/Volumes/Image\ Volume/set-vars.sh -v` instead if you want verbose boot.)
8. The Mac will reboot, so boot from the USB stick again.
9. Open Terminal, then run `/Volumes/Image\ Volume/run-installer.sh`. This will inject the Hax dylib and start the installer. Come back in an hour or two and you should be at the macOS setup region prompt!

This won't fix any post-installation issues, like nonfunctioning Wi-Fi or removing telemetry on systems with Penryn CPUs, but at least it will get a basic installation done on 2011/2012/2013 Macs. I don't expect USB support (necessary for keyboard and trackpad) to work on 2010 or earlier MacBooks right now, but I have not done any testing on those yet.

If you want to undo the patcher's changes to boot-args and csrutil settings, then boot from the USB stick, open Terminal, and run `/Volumes/Image\ Volume/reset-vars.sh`.

The best way to remove the patch from the USB stick is to redo `createinstallmedia`, but if you are working on patcher development or otherwise need a faster way to do it, run `unpatch.sh`.
