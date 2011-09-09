# Scrabble Solver

This is a command line Scrabble solver written in Ruby. Its purpose is to find
all of the possible words given a set of tiles and some optional arguments.

# Installation

Dead simple. you need to have Ruby 1.9.2 installed on your system and then just
execute:

    $ gem install scrabble-solver

# Usage

## Basic

Let's start with the basics, a simple set of tiles:

    $ scrabble-solver tehre

This will return a list of words, among them will be "there", "three", "thee"
and so on.

## Controlling length

If you only want words that are longer than 5 letters returned, that's easy:

    $ scrabble-solver tehre --longer-than 5

If you only want words that are *shorter* than 4 letters, that's easy too:

    $ scrabble-solver tehre --shorter-than 4

You can, of course, combine these if you want:

    $ scrabble-solver tehre --shorter-than 6 --longer-than 3

## Filtering by starts-with and ends-with

This is pretty self explanatory. If you only want words that start with "th",
you would do something like this:

    $ scrabble-solver ree --starts-with th

And the same goes for ends-with:

    $ scrabble-solver teh --ends-with re

## Blank tiles (wildcards)

Got a blank tile? No problem!

    $ scrabble-solver "tehre?"

You need to wrap the tiles you have in double quotes, otherwise the terminal
will shout at you. It doesn't matter where you put the question mark(s), they
will register fine wherever you put them and you can have as many as you want.

## Being specific

Say you've got a really sweet triple letter lined up that will only work if
your Z is the first letter in the word, check this out:

    $ scrabble-solver loogsti --contains z --at 1

The `--contains` flag works without the `--at` flag as well (but not vice versa).
If you want to search for a word that contains a specific sequence of letters at
any position, use `--contains` without specifing `--at`.

    $ scrabble-solver pers --contains li

Returns words like 'lisp' and 'pliers'.

# Word lists

This current version uses the standard Unix word list, but it is designed in
such a way that you can use whatever word list you please.

To specify a new word file, you would do the following:

    $ scrabble-solver letters --word-file /path/to/new/word/file.txt

The word file needs to be a file that contains a list of words, one word per
line. The words can be whatever you want, the solver really doesn't care.
