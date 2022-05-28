# Marlin Configuration

I based the Marlin configuration on a fairly modern config for the [Simple Metal with Rev F PrintrBoard](https://github.com/Printrbot/printrboardmodernmarlin/blob/master/Simple_Metal/RevFv1.0_Printrbot_Simple_Metal_.hex). They're pretty close already, but some changes were needed, plus additional config based on newer options in Marlin.

The files were generated with [Marlin Config]. If you're going to build this firmware yourself, you'll want to replace the `platformio.ini`, `Configuration.h` and `Configuration_adv.h` files in the Marlin repo that it clones. I also recommend using the production branch, rather than hot_fixes.

I had to update the `platformio.ini` file that Marlin Config brought in a little, since it was pointing to the wrong env to build for the at90usb1286 on the PrintrBoard.