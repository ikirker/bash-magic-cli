# bash-magic-cli

This is a work-in-progress bash reimplementation of [@slackhq](https://github.com/slackhq/)'s [magic-cli](https://github.com/slackhq/magic-cli).

Some of the information below is planned rather than current.

The idea is to make a collection of related commands in separate scripts look like one command in one script. I originally started reimplementing it because on the HPC clusters we work on we change up environment variables a lot, so especially things that depend on scripting languages can break if something becomes not available or changes version from the one the author expected. Originally I started it in Golang, because this would give a static binary that would be impervious enough, but doing it in bash instead seemed easier to update on the clusters.

## Usage

This script itself has two subcommands: `list`, and `help`.

The `help` subcommand prints out information about the script. *(Not yet implemented, wanted to nail down some minor details.)*

The `list` subcommand will attempt to find other executable files with names beginning with the name of the script, in the same directory. It will then attempt to work out how to get a `whatis` statement from each one: for scripts, it will pull out the second line and, if it's a comment, display it; for ELF binaries, it will try to run the command with a `-w` option. (I'm still not sure whether this is a good idea.) The results of these will be displayed next to the command's name.

Trying to use any other subcommand will try to run an executable file with the name `script-subcommand` from the same directory as the script (i.e. one the `list` subcommand would display).

## Todo

 * Tests
 * Help information
 * Tweaking command line handling
 * Adding debug flag
