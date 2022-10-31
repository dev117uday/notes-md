# Linux Commands Part 5 - 8

Tags: linux-com-book

## What are commands

* An executable program
* A program built into the shell itself
* A shell function
* A alias

## Commands

* to know command is of which type : `type command`
* to the exact location of executable : `which ls`
* in bash, to get info regarding shell built-ins : `help cd`
* to display program’s manual page : `man program`
* to search the list of man pages for possible matches based on a search term

```bash
-> apropos partition

#output : 
addpart (8)          - tell the kernel about the existence of a partition
cfdisk (8)           - display or manipulate a disk partition table
cgdisk (8)           - Curses-based GUID partition table (GPT) manipulator
delpart (8)          - tell the kernel to forget about a partition
fdisk (8)            - manipulate disk partition table
...
```

* to display one-line manual page description : `whatis ls`
* alternative to man page : `info coreutils`
* to create alias command : `alias foo=”cd programm && code .”`

## Input Output Commands

* to redirect standard output to a file :
* `[me@linuxbox ~]$ ls -l /usr/bin > ls-output.txt`
* “>” also clears the whole file and adds the new content
* “>>” will append the content to the file at the end
* Error message aren’t send to file unless specified in the command, they are sent to standard error

There are 3 types of file streams

* Input
* Output
* Error

```bash
# redirect standard error to file
ls -l /bin/usr 2> ls-error.txt

# redirecting standard output to standard error
ls -l /bin/usr > ls-output.txt 2>&1

# modern way to redirect output
ls -l /bin/usr &> ls-output.txt

# disposing unwanted output
ls -l /bin/usr 2> /dev/null
```

## Pipelines

* The capability of commands to read data from standard input and send to standard output.
* to view a long output : `ls -l /usr/bin | less`
* Pipelines are used along with filter
* Ex : `ls -l /usr/bin | sort | less`

### The Difference Between > and |

Simply put, the redirection operator connects a command with a file, while the pipeline operator connects the output of one command with the input of a second command.

* `uniq` is used to remove duplicate lines, mostly placed after sort
* `wc` : to print Print Line, Word, and Byte Counts : `wc names.txt`
* grep to filter out using keyword : `ls /bin /usr/bin | sort | uniq | grep zip`
* `head` to print the first part of file
  * `-n x` to print first/last x lines
* `tail` to print the last part of file
  * `-f` to keep watching file for changes
* `tee` : program reads standard input and copies it to both standard output (allowing the data to continue down the pipeline) and to one or more files

## The world of Echo

* print something to terminal

```bash
➜  ~ echo "hello world"
hello world

# print file starting with D
➜  ~ echo D*
Desktop Documents Downloads

# print upper case
[me@linuxbox ~]$ echo [[:upper:]]*
Desktop Documents Music Pictures Public Templates Videos

# print matching directories
[me@linuxbox ~]$ echo /usr/*/share
/usr/kerberos/share /usr/local/share
```

### Arithmetic Expression

```bash
➜  ~ echo $((2 + 2))
4

➜  ~ echo $(($((5**2)) * 3))
75
```

### Brace Expression

```bash
➜ ~ echo Front-{A,B,C}-Back
Front-A-Back Front-B-Back Front-C-Back

➜ ~ echo Number_{1..5}
Number_1 Number_2 Number_3 Number_4 Number_5

# In bash version 4.0 and newer, 
# integers may also be zero-padded like so:
[me@linuxbox ~]$ echo {01..15}
01 02 03 04 05 06 07 08 09 10 11 12 13 14 15

# with numbers
[me@linuxbox ~]$ echo {001..15}
001 002 003 004 005 006 007 008 009 010 011 012 013 014 015

# Here is a range of letters in reverse order
[me@linuxbox ~]$ echo {Z..A}
Z Y X W V U T S R Q P O N M L K J I H G F E D C B A

# Brace expansions may be nested.
[me@linuxbox ~]$ echo a{A{1,2},B{3,4}}b
aA1b aA2b aB3b aB4b

# making dir with braces
- ~ mkdir {2007..2009}-{01..12}
[me@linuxbox Photos]$ ls
2007-01 2007-07 2008-01 2008-07 2009-01 2009-07
2007-02 2007-08 2008-02 2008-08 2009-02 2009-08
2007-03 2007-09 2008-03 2008-09 2009-03 2009-09
2007-04 2007-10 2008-04 2008-10 2009-04 2009-10
2007-05 2007-11 2008-05 2008-11 2009-05 2009-11
2007-06 2007-12 2008-06 2008-12 2009-06 2009-12
```

* use **“”** to print the string as it is
* use \*_\*_ to as escape character
* `!200` will give the command in history at line 200
