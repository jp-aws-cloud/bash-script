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

For this change to be applied to every shell you open, add it to a file that the shell will source when it
is invoked. This will be `.bash_profile`, `.bashrc`, or `.profile` depending on how bash is invoked. These
files are sourced only for interactive shells, not for scripts.

## Creating the File and Running the Script

Usually you would use a text editor to create your program, but for a simple script like this, it’s not
necessary to call up an editor. You can create the file from the command line using redirection:

```sh
echo echo Hello, World! > bin/hw
```

`The greater-than sign (>) tells the shell to send the output of a command to the specified file, rather
than to the terminal.`

The program can now be run by calling it as an argument to the shell command:

```bash
bash bin/hw
```

That works, but it’s not entirely satisfactory. You want to be able to type hw, without having to
precede it with bash, and have the command executed. To do that, give the file execute permissions:

```sh
chmod +x bin/hw
```

Now the command can be run using just its name:

```bash
$ hw
Hello, World!
```

### Building a Better “Hello, World!”

Earlier in the chapter you created a script using redirection. That script was, to say the least, minimalist.
All programs, even a one-liner, require documentation. Information should include at least the author,
the date, and a description of the command. Open the file bin/hw in your text editor, and add the
information in Listing 1-1 using comments.

```sh
# Listing 1-1. hw

#!/bin/bash
#: Title : hw
#: Date : 2008-11-26
#: Author : "Chris F.A. Johnson" <shell@cfajohnson.com>
#: Version : 1.0
#: Description : print Hello, World!
#: Options : None
printf "%s\n" "Hello, World!"

```

Comments begin with an `octothorpe`, or `hash (#)`, at the beginning of a word and continue until the
end of the line. The shell ignores them. I often add a character after the hash to indicate the type of
comment. I can then search the file for the type I want, ignoring other comments.
The first line is a special type of comment called a `shebang` or `hash-bang`. It tells the system which
interpreter to use to execute the file. The characters `#!` must appear at the very beginning of the first line;
in other words, they must be the `first two bytes` of the file for it to be recognized. 

### Summary
The following are the commands, concepts, and variables you learned in this chapter.
Commands

- pwd: Prints the name of the current working directory
- cd: Changes the shell’s working directory
- echo: Prints arguments separated by a space and terminated by a newline
- type: Displays information about a command
- mkdir: Creates a new directory
- chmod: Modifies the permissions of a file
- source: a.k.a. . (dot): executes a script in the current shell environment
- printf: Prints the arguments as specified by a format string
