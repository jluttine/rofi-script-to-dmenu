# Rofi Script to Dmenu

A simple executable that can run a rofi script with dmenu (or with dmenu mode of
rofi).

Just give a normal rofi script **that can be used in rofi script mode** as an
argument and rofi-script-to-dmenu will take care of the rest. It'll also pass
any options to dmenu. In addition, mode options printed with the special
rofi-script syntax by starting a line with the null byte are handled correctly
and passed to rofi/dmenu. See rofi-script man page for more information.

**Note that this tool will not work with many rofi scripts that are stand-alone
scripts (i.e., they call rofi themselves) instead of being written for the rofi
script mode.**


## Usage

```
rofi-script-to-dmenu - run a rofi script with dmenu mode

Usage: rofi-script-to-dmenu SCRIPT [OPTIONS]

Given a script SCRIPT that works in Rofi script mode, rofi-script-to-dmenu runs
it with dmenu mode. The first argument must the script but other arguments and
options are passed to dmenu (or rofi) as such.

For example, given the rofi-file-browser.sh script in Rofi repository, you can
run it as follows in dmenu mode:

  rofi-script-to-dmenu rofi-file-browser.sh -i -p 'Cool File Browser'

If you want to pass arguments to your script, just enclose the script and its
arguments with quotes.

If no arguments are given, this help text is shown.

If rofi executable is in PATH, it is used (with -dmenu option), otherwise dmenu
executable is used.
```


## `ROFI_SCRIPT_TO_DMENU_AUTOEXIT`

Note that rofi works in script mode so that it exits when the script doesn't
give any output, but it will always show up after the first script invocation
whether or not the script had any output. By default, this tool works similarly,
but if you set environment variable `ROFI_SCRIPT_TO_DMENU_AUTOEXIT=1`, then
dmenu/rofi will not show up at all if the script had empty output in the first
run. This might be useful, for instance, if you browse some tree structure and
just want the script to do its job when reaching a leaf node (e.g., open the
selected file). For more details, see:
https://github.com/davatorium/rofi/issues/1093


## Why?

There are a few reasons why you might be interested in this small tool:

- You want to use dmenu options with a rofi script. That's not possible when
  running the script in rofi script mode.

- You don't have rofi available and want to use dmenu, but still you found some
  interesting rofi scripts.

- You want to rofi to exit if the script doesn't give any output on the first
  call.

- You don't know how to run rofi scripts (well, you should learn!) so this tool
  might make it simpler for you.


## Copyright

Copyright (c) 2020 Jaakko Luttinen

MIT License
