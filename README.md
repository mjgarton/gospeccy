# GoSpeccy - A naive ZX Spectrum 48k Emulator

GoSpeccy is yet another ZX Spectrum (Speccy for friends) Emulator. The
interesting fact is that it is written in Go and - AFAIK - it's the
first Spectrum/Z80 emulator coded with the new language by Google.

There are a lot of ZX Spectrum emulators around so, why reinventing
the wheel? Well, mainly for
[amarcord](http://en.wikipedia.org/wiki/Amarcord) reasons and then
because it was a great learning experience about emulators for me :)
And it was a good chance to write something real with Go.

Coding an emulator in Go is very enjoyable. The language is simple,
pragmatic and fast (well... fast enough to run a Z80 emulator!). It
has a lot of features that help in emulators development:
 
* it has "low-level" similarities with C being *a lot* more effective
  than C!

* it is strong-typed and type safe so you are aware about errors at
  compile-time

* it is garbage collected so you haven't to worry about memory leaks

* it has an int16 built-in type that helps dealing with 8/16 bit
  machines

* it has goroutines that help handling emulator events (keyboard
  events for example)

The Zilog Z80 emulation is the core of GoSpeccy. The CPU emulation
code is generated using the <tt>z80.pl</tt> script shipped with
[FUSE](http://fuse-emulator.sourceforge.net/) (one of the best ZX
Spectrum emulator around). The script has been hacked to generate Go
code rather than C code.

Another source of inspiration was
[JSSpeccy](http://matt.west.co.tt/spectrum/jsspeccy/), a neat
Javascript Speccy emulator.

The Z80 emulation is tested against the excellent test-suite shipped
with FUSE.

If you like this software, please watch it on
[github](http://github.com/remogatto/gospeccy)! Seeing a growing
number of watchers is an excellent motivation for me to keep up this
work :) Bug reports and testing are also appreciated! And don't forget
to fork and send me patches, of course ;)

# Features

* Complete Zilog Z80 emulation
* SNA format support
* SDL backend
* 2x scaler and fullscreen (to be improved)

# Dependencies

* [banthar/Go-SDL](http://github.com/banthar/Go-SDL)
* [0xe2-0x9a-0x9b/Go-PerfEvents](http://github.com/0xe2-0x9a-0x9b/Go-PerfEvents)

On Ubuntu Linux you'll need to install the following packages using synaptic:

    sudo apt-get install libsdl1.2-dev libsdl-mixer1.2-dev libsdl-image1.2-dev libsdl-ttf2.0-dev

# Quick start

First of all, be sure to install the dependencies. Then:

    git clone http://github.com/remogatto/gospeccy.git
    cd gospeccy
    make install
    gospeccy -doubled # Execute in a doubled size window

Now try press the following keys:

    p
    CTRL+p
    hello world
    CTRL+p
    RETURN

And see your shining new ZX Spectrum 48k responding :)

Tips: to simulate a backspace hit:

    LEFT SHIFT+0

For a nice picture of the speccy keyboard layout visit this [page](http://www.guybrush.demon.co.uk/spectrum/docs/Basic.htm).

To load a SNA rom:

    gospeccy -doubled image.sna

And if you're curious to see what this glorious machine can do despite
of its limited graphics capabilities, try the nice
[Fire104b](http://pouet.net/prod.php?which=54076) intro by Andrew
Gerrand included in the gospeccy distribution! In the gospeccy folder,
run:

    gospeccy -doubled snapshots/Syntax09nF.sna

# Key bindings

    Host computer   Zx Spectrum
    ---------------------------
    CTRL            SYMBOL SHIFT
    LEFT SHIFT      CAPS SHIFT
    [a-z0-9]        [A-Z0-9]
    SPACE           SPACE

For more info about keybindings see <tt>spectrum/keyboard.go</tt>

# Propretary ROMs

Generally, propretary roms are protected by copyright so none of them
is included in GoSpeccy (with the exception of the 48k rom that can be
freely distributed). BTW, you can find tons of roms for the ZX
Spectrum on the Internet. Take a look at JSSpeccy
[svn](http://svn.matt.west.co.tt/svn/jsspec/trunk/snapshots/)
repository.

# Screenshots

![Batty running on GoSpeccy](http://sites.google.com/site/remogatto/batty.png)

# TODO

* Add sound emulation
* Improve memory contention
* Add support for more file formats (take a look [here](http://www.worldofspectrum.org/faq/reference/formats.htm))
* Better general performances
* Add more filters and improve the scaler
* Add new backends (exp/draw?)

# Contacts

* andrea.fazzi@alcacoop.it
* http://twitter.com/remogatto
* http://freecella.blogspot.com

# LICENSE

Copyright (c) 2010 Andrea Fazzi

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
"Software"), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE
LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION
OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION
WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

