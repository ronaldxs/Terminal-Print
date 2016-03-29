# Terminal::Print

## History

At first I thought I might try writing a NativeCall wrapper around ncurses. Then I realized that there is absolutely no reason to fight a C library which has mostly bolted on Unicode when I can do it in Pure Perl 6, with native Unicode goodness.

## Usage

Right now it only provides a grid with some nice access semantics.

````
  my $screen = Terminal::Print.new;

  $screen[9][23] = "%";         # prints the escape sequence to put '%' on line 9 column 23
  $screen[9][23];               # returns "%"
  $screen[9][23].print-cell     # prints "%" on the 23rd column of the 9th row

  $screen(9,23,"%");            # another way, designed for golfing or simpler expression
````

(Please note that these are are still subject to change as the library develops further).

Terminal::Print intends to provide the essential underpinnings of command-line printing, to be the fuel for the fire, so to speak, for libraries which might aim towards 'command-line user interfaces' (CUI), asynchronous monitoring, rogue-like adventures, screensavers, video art, etc.

Check out some animations:
````
perl6 -Ilib examples/show-love.p6
perl6 -Ilib examples/zig-zag.p6
````

Additionally, if your terminal supports ANSI escape codes, then you may set the environment variable `USE_ANSI` to a non-empty value.


# STATUS: ALPHA

This module is currently under nourished. It hungers for a proper test suite, documentation, and a truly crash free asynchronous implementation.

The core of the 'tricky' parts is all there, however, in `Terminal::Print::Commands`. With that you can wrap your own printer very easily.


Copyright 2015-2016, John Haltiwanger. Released under the Artistic License 2.0.
