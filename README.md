# Tmox (Terminal Monoplexer)

Tmox spawns a shell detached from the current terminal. The detached shell stays alive even after the terminal is closed. It's _almost_ equivalent to [Tmux](https://github.com/tmux/tmux) that spawns multiple detached shells ("**multi**plexer"). Instead, Tmox detaches only _one_ shell; hence "**mono**plexer".

## Why?

Tmox was designed for a peculiar setup as follows.

 - You don't have `root`.
 - You can't install any program.
 - You must hold the shell alive even after closing the terminal.

A very simple example of this peculiar setup would be using a cluster as a non-admin, where (for some reason) you need to keep your shell alive to maintain the connection to one of the cluster nodes but have no privilege to install extra programs to do so and no authority to make _you_ to be able to use the node anyway.

# Usage

 - Run `bash tmox` to spawn and enter a detached shell.
 - Press "Ctrl-Q" to detach from the shell (still alive).
 - Run `bash tmox` _again_ to re-enter the detached shell.
 - Type `exit` to close the detached shell.
