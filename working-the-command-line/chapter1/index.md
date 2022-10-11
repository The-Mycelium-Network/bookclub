# Chapter 01 – "Just open the terminal..."

## Terminal application options

### Linux

- [Gnome Terminal](https://help.gnome.org/users/gnome-terminal/stable/)

There are also [some alternatives](https://www.slant.co/options/2442/alternatives/~gnome-terminal-alternatives) you can explore.

### Windows

- Command Prompt
- [Powershell](https://learn.microsoft.com/en-us/powershell/)
- [WSL[2]](https://learn.microsoft.com/en-us/windows/wsl/about) aka Windows Subsystem for Linux version 1 and 2
- [Git BASH](https://www.atlassian.com/git/tutorials/git-bash)

For Windows users, you can get [Windows Terminal](https://github.com/microsoft/terminal), a multi-tabbed terminal emulator, and integrate several shells into it.

You can also customize your terminal on Windows with [Oh My Posh](https://learn.microsoft.com/pt-br/windows/terminal/tutorials/custom-prompt-setup).

### macOS

- Built in [macOS terminal](https://support.apple.com/en-za/guide/terminal/welcome/mac)
- [iTerm2](https://iterm2.com/)

### Cross platform

- [Hyper terminal](https://hyper.is/)

## Getting help

### `man`

In the terminal type `man <command>` to bring up the documentation for the specified command, for example:

```bash
man ls
```

If you're using Git Bash, you should use the `--help` flag instead to achieve the same result.

```bash
ls --help
```

## Interacting with the file system

### `ls`

The most basic way to list the contents of the current directory is to type `ls`.

```bash
❯ ls
chapter1 chapter3
```

Taking it up a level we run `ls -lF`

```bash
❯ ls -lF
total 0
drwxr-xr-x  2 schalkneethling  staff   64 Sep 18 13:01 chapter1/
drwxr-xr-x  4 schalkneethling  staff  128 Sep  5 01:14 chapter3/
```

### `-l`

> The lowercase letter “ell”.) List files in the long format, as described in the The Long Format subsection below.

There is more to the definition of "The Long Format" that you can find in the manual page but, the short of it is as follows:

> If the -l option is given, the following information is displayed for each file:
>
> - file mode,
> - number of links,
> - owner name,
> - group name,
> - number of bytes in the file,
> - abbreviated month,
> - day-of-month file was last modified,
> - hour file last modified,
> - minute file last modified,
> - and the pathname.

#### Understanding the permission details

The first column, on the left, will present a series of letters and dashes that correspond to the file permissions.

The first character is the file type (`-` for a regular file, `d` for a directory, and `l` for a symlink). Then, there are three groups of special characters regarding the permissions of the `user`, the `group`, and the `other` categories. Each trio is composed of the letters `r`, `w`, and `x`, which stands for read, write and execute permissions, respectively. When that category doesn't have a certain type of permission, the letter is replaced by a `-`.

> For instance, a `drwxr-xr-x` code indicates that the file is a directory, the `user` has read, write and execute permissions, while the `group` and the `other` categories, only have permissions to read or execute.

### `-F` or --classify

> Display a slash (‘/’) immediately after each pathname that is a directory, an asterisk (‘\*’) after each that is executable, an at sign (‘@’) after each symbolic link, an equals sign (‘=’) after each socket, a percent sign (‘%’) after each whiteout, and a vertical bar (‘|’) after each that is a FIFO.

### `-t`

> Sort by descending time modified (most recently modified first). If two files have the same modification timestamp, sort their names in ascending lexicographical order. The -r option reverses both of these sort orders.

```bash
❯ ls -lt
total 0
drwxr-xr-x  2 schalkneethling  staff   64 Sep 18 13:01 chapter1
drwxr-xr-x  4 schalkneethling  staff  128 Sep  5 01:14 chapter3
```

### `-r`

Reverse the order of the sort. Above we ran the command `ls -lt`. If we then run the following, `ls -ltr` on the same folder, the output changes as shown below.

```bash
❯ ls -ltr
total 0
drwxr-xr-x  4 schalkneethling  staff  128 Sep  5 01:14 chapter3
drwxr-xr-x  2 schalkneethling  staff   64 Sep 18 13:01 chapter1
```

### `cd`

You move up and down the directory tree (folders) by using the `cd` (short for change directory) command.

```plain
working-command-line
-- chapter1
-- chapter3
```

When inside `working-command-line` type `cd chapter1` will move you into the `chapter1` directory. To move back up to the parent directory, enter `cd ../`. For each level you want to move up the tree, add another `../`. So, to get to the parent directory of `working-command-line` from within `chapter1`, type `cd ../../`.

When a directory or filename includes space characters, you need to either wrap the entire name in double quotes or, escape each space with a backslash.

```bash
cd "folder with spaces"
cd file\ with\ spaces.png
```

## Command history

To see a history of the command you ran in your terminal type `history`. There will be a LOT there but there are some useful shortcuts to work with this history.

One way of searching your history is by pressing `Ctrl+R`

```bash
❯
bck-i-search: _ # Start typing your search. 
Once you find the command, press enter to execute it
```

> NOTE: You can press `Ctrl+C` to exit out of search mode.

Let’s say we run `ls -l` and press enter but then realize we wanted to run `ls -lt`. You could type it out or you can do something like this:

```bash
ls -l # press enter
!! # press enter (Also knows as bang bang)
# You will be presented with your last command
ls -l
# just add the `t` and press enter
ls -lt
```

Now, let’s see you believe a specific file you are looking for is in the `chapter3` directory, you can `cd` into it and then run `ls` or, you can do something like this:

```bash
ls -lt chapter3
# This output a listing of the directory contents
total 16
-rw-r--r--  1 schalkneethling  staff  1088 Sep  5 01:15 network-ext.log
-rw-r--r--  1 schalkneethling  staff   687 Sep  4 21:37 network.log
# To get the last argument of the previous command you use !$
cd !$ # press enter (Also knows as pling dollar)
# You will now see the following at your prompt
cd chapter3 # press enter
# To quickly move back to the last directory you were in, type:
cd - # In this case it will take you back to working-command-line
```
