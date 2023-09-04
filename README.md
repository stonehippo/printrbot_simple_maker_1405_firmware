# printrbot_simple_maker_1405_firmware
Updated Marlin firmware for the PrintrBot Simple Maker 1405 3D printer.

## Installing a modern Marlin firmware on PrintrBot Simple Maker 1405

My first 3D printer is a PrintrBot Simple Maker, a little 3D printer kit from the early days of DIY RepRap. I've had this little mostly plywood printer for years, and it taught me a lot about additive manufacturing and 3D design and printing. I have updated and upgraded it multiple times, and like a robotic Ship of Theseus, I've replaced enough components that it's fair to say the device I'm using now is barely the same one I assembled when I first opened that box of parts. The extruder is now a pretty nice aluminum unit (the second version I've installed) and a far cry from the laser-cut assembly I started with. The chassis was upgraded from the original Maker design to the newer 1405 version, and the PrintrBoard is a Rev F5 (I still have the Rev D PrintrBoard I installed as a replacement when the original died).

I have a lot of affection for my PrintrBot, even though I have a more modern and capable printer, and I still use it from time to time (for small stuff, since it's only got a 100^3 build volume). One component of the printer that could use some love is the PrintrBoard firmware. I have the last version of the original PrintrBot fork on there now, which dates back to 2015. Marlin has come a long way in the past seven years, and I could get better prints out of the Simple Maker if I upgraded.

Of course, this is easier said than done. ;-)

## Resources

- [Marline Firmware](https://marlinfw.org) - The firmware that makes it all go
- [Original PrintrBot Marlin firmware repo](https://github.com/Printrbot/Marlin) - the Marlin 1 fork that originally shipped with PrintrBot units
- [Modern Marlin for PrintrBots repo](https://github.com/Printrbot/printrboardmodernmarlin) - configurations for newer versions of Marlin
- [Marlin Config](https://github.com/akaJes/marlin-config) - A useful tool for configuring and compile Marlin
- [PrintrBot FirmwareUpdatr](https://github.com/stonehippo/FirmwareUpdatr) - a macOS tool for uploading firmware to PrintrBot printers (this is my fork of the original repo)

## Building a new Marlin for the Simple Maker 1405

The repo that has modern Marlin configs does not have a configuration for the Simple Maker 1405 (not really sure why). However, it does have the Simple Metal, a closely related printer, and I could use that as the based for creating a config for the 1405. I startd with xxx.

## Fixing FirmwareUpdatr

FirmwareUpdatr is a simple enough tool to use, but it's been a while since it was updated, and it's kinda broken now. When I first went to try it with the newly built firmware, it seemed to pop up for a second, and then shut down. A check of the macOS console confirmed that the app was starting up and then failing. I realized that it was probably pretty badly out of date and no longer fully compatible with recent macOS versions.

FirmwareUpdatr has a few dependencies. Two of them, cocoaDialog and dfu-programmer, turned out to be the issue. The version of cocoaDialog bundled into the app no longer worked. Fortunately, the last beta seems to work, so I just swapped it out in the bundle.

The version of dfu-programmer was also broken. To fix that took a little more work, since I had to compile a new version of that cli tool (with changes reflected in [my fork](https://github.com/stonehippo/dfu-programmer)). Once again, a little surgery on the FirmwareUpdater package, and I had a working tool again.
