# Textractor

[Español](https://github.com/Artikash/Textractor/blob/master/README_ES.md)<br>
[简体中文](https://github.com/Artikash/Textractor/blob/master/README_SC.md)<br>
[日本語](https://github.com/Artikash/Textractor/blob/master/README_JP.md)

## [Tutorial Video](https://youtu.be/eecEOacF6mw)

[![Donate](https://www.paypalobjects.com/en_US/i/btn/btn_donate_SM.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=akashmozumdar%40gmail.com&item_name=Textractor%20development&currency_code=USD)

## Overview

**Textractor** (a.k.a. NextHooker) is an open-source x86/x64 text hooker for Windows/Wine based off of [ITHVNR](http://www.hongfire.com/forum/showthread.php/438331-ITHVNR-ITH-with-the-VNR-engine).<br>

![How it looks](https://media.discordapp.net/attachments/330538905072041994/539414661796200448/unknown.png?width=1072&height=398)

## Downloads

Releases of Textractor can be found [here](https://github.com/Artikash/Textractor/releases).<br>
Previous releases of ITHVNR can be found [here](https://github.com/mireado/ITHVNR/releases).<br>
If you get a dll missing error, you probably need to (re)install the [Microsoft Visual C++ Redistributable](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads).

## Features

- Highly extensible
- Auto hook many game engines (including some not supported by VNR!)
- Hook text using /H "hook" codes (most AGTH codes supported)
- Directly extract text using /R "read" codes

## Support

Please let me know of any bugs, games that Textractor has trouble hooking, feature requests, or other suggestions.<br>
If you have trouble hooking a game please email me a place where I can freely download it, or gift it to me on [Steam](https://steamcommunity.com/profiles/76561198097566313/).

## Extensions

See my [Example Extension project](https://github.com/Artikash/ExampleExtension) to see how to build an extension.<br>
See the extensions folder for examples of what extensions can do. 

## Contributing

All contributions are appreciated! Please email (no, I'm not busy!) me at akashmozumdar@gmail.com if you have any questions about the codebase.<br>
You should use the standard process of making a pull request (fork, branch, commit changes, make PR from your branch to my master).<br>
Contributing a translation is easy: just translate the strings in text.cpp as well as this README.

## Compiling

Before compiling *Textractor*, you should get Visual Studio with CMake support, as well as Qt version 5.11<br>
You should then be able to simply open the folder in Visual Studio, and build. Run Textractor.exe.

## Project Architecture

The host (see GUI/host folder) injects vnrhook.dll (created from the vnrhook folder) into the target process and connects to it via 2 pipe files.<br>
Host writes to hostPipe, vnrhook writes to hookPipe.<br>
vnrhook waits for the pipe to be connected, then injects a few instructions into any text outputting functions (e.g. TextOut, GetGlyphOutline) that cause their input to be sent through the pipe.<br>
Additional information about hooks is shared through a file view (a.k.a. section object) that is mapped to a reference to the TextHook class.<br>
The text that the host receives through the pipe is then processed a little before being dispatched back to the GUI.<br>
Finally, the GUI dispatches the text to extensions before displaying it.

## Developers

If you're on this list and want your link changed let me know.
- Textractor made by [Me](https://github.com/Artikash) and [DoumanAsh](https://github.com/DoumanAsh)
- Spanish translation by [scese250](https://github.com/scese250)
- Turkish translation by niisokusu
- Simplified Chinese translation by [tinyAdapter](https://github.com/tinyAdapter)
- ITHVNR updated by [mireado](https://github.com/mireado) and [Eguni](https://github.com/Eguni)
- ITHVNR originally made by [Stomp](http://www.hongfire.com/forum/member/325894-stomp)
- VNR engine made by [jichi](https://archive.is/prJwr)
- ITH updated by [Andys](https://github.com/AndyScull)
- ITH originally made by [kaosu](http://www.hongfire.com/forum/member/562651-kaosu)
- Locale Emulator library made by [xupefei](https://github.com/xupefei)
- MinHook library made by [TsudaKageyu](https://github.com/TsudaKageyu)

## Special Thanks

- Everybody adding issues!
