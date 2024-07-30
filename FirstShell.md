# Your First Shell Program

A shell script is a file containing one or more commands that you would type on the command line.

You should be in your home directory, which you can find in the variable $HOME:

```bash
echo $HOME
```

You can find the current directory with either the pwd command or the PWD variable:

```sh
pwd
echo "$PWD"
```

If you are not in your home directory, you can get there by typing cd and pressing Enter at the shell
prompt.

## The Code

The code is nothing more than this:

```sh
echo Hello, World!
```

## Selecting a Directory for the Script

When the shell is given the name of a command to execute, it looks for that name in the directories listed
in the PATH variable. This variable contains a colon-separated list of directories that contain executable
commands. This is a typical value for $PATH:

```sh
/bin:/usr/bin:/usr/local/bin:/usr/games
```

If your program is not in one of the PATH directories, you must give a pathname, either absolute or
relative, for bash to find it. An absolute pathname gives the location from the root of the filesystem, such
as `/home/chris/bin/hw;` a relative pathname is given in relation to the current working directory (which
should currently be your home directory), as in `bin/hw`.

Commands are usually stored in directories named bin, and a user’s personal programs are stored
in a bin subdirectory in the $HOME directory. To create that directory, use this command:

```bash
mkdir bin
```

Now that it exists, it must be added to the PATH variable:

```bash
PATH=$PATH:$HOME/bin
```
