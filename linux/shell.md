# Shell programming

## Getting Started with Shell Programming

#### 1.1 Hello  World

**Printing Hello World**

```
echo "Hello World"
echo hello world
```

`echo` is a Bash builtin command that writes the arguments it receives to the standard output. It appends a newline to the output, by default.

**Non-interactive shell**

*   Create a file with `.sh` extension using

    ```
    touch try.sh
    ```
*   Make the script executable

    ```
    chmod +x try.sh
    ```

    `+x` makes the file executable
*   open the file in nano by

    ```
    nano try.sh
    ```

    Or you can use vim, sublime, VScode or any other text editor you like.
*   Inside the file, add

    ```
    #!/bin/bash
    echo "Hello World"
    ```

    Line 1: The first line of the script must start with the character sequence #!, referred to as shebang

    * The shebang instructs the operating system to run /bin/bash, the Bash shell, passing it the script's path as an argument
*   Run the file using

    ```
    ./try.sh
    ```

    OR you can use any of the following

    ```
    ./hello-world.sh 
    /bin/bash hello-world.sh
    bash hello-world.sh 
    sh hello-world.sh
    ```

**Note** : Forgetting to apply execute permission on the file, i.e., `chmod +x hello-world.sh`, resulting in the output of `./hello-world.sh`: `Permission denied`

#### 1.2 Hello World using Variables

* Create a new file called `hello.sh`
*   Add

    ```
    #!/bin/bash
    whom_variable="World"
    printf "Hello, %s\n" "$whom_variable"
    ```

    **Note :** spaces cannot be used around the `=` assignment operator

#### 1.3 Hello World with User Input

**1.3.1 Reading from console**

```
echo "Who are you?"
read name
echo "Hello, $name.
```

`read` will **read** input given in a new line until the `enter` key is not pressed and will store the value in variable mentioned after the keyword.

**1.3.2 Formatting String**

```
echo "What are you doing?"
read action
echo "You are ${action}ing."
```

#### 1.4 Importance of Quoting in String

There are two types of quoting: \\

* **Weak**: uses double quotes: `"` \\
* **Strong**: uses single quotes: `'`
*   If you want to bash to expand your argument, you can use **Weak Quoting**:

    ```
    #!/bin/bash
    world="World"
    echo "Hello $world"
    #> Hello World
    ```
*   If you don't want to bash to expand your argument, you can use **Strong Quoting**:

    ```
    world="World"
    echo 'Hello $world'
    #> Hello $world
    ```

#### 1.5  Hello World in "Debug" mode

To see which line is running, you can use Debug mode

* Create a new file with simple echo hello world
*   Run the Script using

    ```
    $ bash -x hello.sh
    ```

    you will get the following output :

```
$ echo Hello World
$ Hello World
```

**Note** : The -x argument enables you to walk through each line in the script

## Cat & Alias

### Using Cat

**Concatenate files**

This is the primary purpose of `cat` is to concatenate files.

```
cat text1.txt text2.txt > text3.txt
```

This will add the contents of `text1.txt` and `text2.txt` to a new files called `text3.txt`

**Printing the Contents of a File**

```
cat file.txt
```

will print the contents of a file.

If the file contains non-ASCII characters, you can display those characters symbolically with `cat -v` . This can be quite useful for situations where control characters would otherwise be invisible.

Very often, for interactive use, you are better off using an interactive pager like `less` or `more` , though. ( `less` is far more powerful than `more` and it is advised to use `less` more often than `more`)

```
less file.txt
```

In case the content needs to be listed backwards from its end the command tac can be used:

```
tac file.txt
```

If you want to print the contents with line numbers, then use `-n` with cat:

```
cat -n file.txt
```

**Write to a file**

```
cat >file
```

It will let you write the text on terminal which will be saved in a file named file.

```
cat >>file
```

will do the same, except it will append the text to the end of the file.

**N.B:** `Ctrl+D` to end writing text on terminal (Linux)

**Read from standard input**

```
cat < file.txt
```

Output is same as cat file.txt , but it reads the contents of the file from standard input instead of directly from the file.

```
printf "first line\nSecond line\n" | cat -n
```

The echo command before | outputs two lines. The cat command acts on the output to add line numbers.

**Display line numbers with output**

Use the --number flag to print line numbers before each line. Alternatively, `-n` does the same thing.

```
cat --number file
```

To skip empty lines when counting lines, use the `--number -nonblank` , or simply `-b` .

```
cat -b file
```

### Aliasing

Shell aliases are a simple way to create new commands or to wrap existing commands with code of your own. They somewhat overlap with shell functions, which are however more versatile and should therefore often be preferred.

#### Create an Alias

```
alias word='command'
```

Invoking word will run `command`. Any arguments supplied to the alias are simply appended to the target of the alias:

To include multiple commands in the same alias, you can string them together with **&&** . For example:

```
alias print_things='echo "foo" && echo "bar" && echo "baz"'
```

#### Remove an alias

To remove an existing alias, use:

```
unalias {alias_name}
```

#### Bypass an alias

Sometimes you may want to bypass an alias temporarily, without disabling it. To work with a concrete example, consider this alias:

```
alias ls='ls --color=auto'
```

#### The BASH\_ALIASES is an internal bash assoc array

Aliases are named shortcuts of commands, one can define and use in interactive bash instances. They are held in an associative array named BASH\_ALIASES. To use this var in a script, it must be run within an interactive shell

```
#!/bin/bash -li
# note the -li above! -l makes this behave like a login shell
# -i makes it behave like an interactive shell
#
# shopt -s expand_aliases will not work in most cases

echo There are ${#BASH_ALIASES[*]} aliases defined.

for ali in "${!BASH_ALIASES[@]}"; do
printf "alias: %-10s triggers: %s\n" "$ali" "${BASH_ALIASES[$ali]}"
done
```

#### List all Aliases

```
alias -p
```

will list all the current aliases.

## Jobs

### Jobs

* To create an job, just append a single & after the command: `$ sleep 10 &`
* Or run immediately : `sleep 10`
* To bring the Process to the foreground, the command fg is used together with % : `fg %`
*   Killing running jobs

    ```
    $ sleep 10 &
    [1] 20024
    $ kill %1
    [1]+ Terminated                    sleep 10
    ```

## Navigating & Listing

### Navigating Directory

#### Absolute vs relative directories

To change to an absolutely specified directory, use the entire name, starting with a slash /, thus:

```bash
cd /home/username/project/abc
```

If you want to change to a directory near your current on, you can specify a relative location. For example, if you are already in /home/username/project, you can enter the subdirectory abc thus:

```bash
cd abc
```

If you want to go to the directory above the current directory, you can use the alias ...

For example, if you were in `/home/username/project/abc` and wanted to go to `/home/username/project`, then you would do the following:

```bash
cd ..
```

#### Change to the last directory

For the current shell, this takes you to the previous directory that you were in, no matter where it was.

```bash
cd -
```

#### Change to the home directory

The default directory is the home directory `$HOME`, typically `/home/username`,

So `cd` without any directory takes you there

Or you could be more explicit: `cd $HOME`

A shortcut for the home directory is `cd ~`, so that could be used as well.

### Listing Files

| option | description |
| ------ | ----------- |

ls -a | list all files including hidden file starting with '.' ls --color | colored list \[=always/never/auto] ls -d | list directories - with ' _/' ls -F \`add one char of_ /=>@\` | to enteries ls -i | list file's inode index number ls -l | list with long format - show permissions ls -la | list long format including hidden files ls -lh | list long format with readable file size ls -ls | list with long format with file size ls -r | list in reverse order ls -R | list recursively directory tree ls -s | list file size ls -S | sort by file size ls -t | sort by time & date ls -X | sort by extension name |

### List Files in a Long Listing Format

The ls command's `-l` option prints a specified directory's contents in a long listing format. If no directory is specified then, by default, the contents of the current directory are listed.

```bash
ls -l /etc
```

**Example Output:**

```bash
total 1204 
drwxr-xr-x 3 root root 4096 Apr 21 03:44 acpi
-rw-r--r-- 1 root root 3028 Apr 21 03:38 adduser.conf
drwxr-xr-x 2 root root 4096 Jun 11 20:42 alternatives
...
```

The output first displays total, which indicates the total size in blocks of all the files in the listed directory. It then displays eight columns of information for each file in the listed directory.

#### List the Ten Most Recently Modified Files

The following will list up to ten of the most recently modified files in the current directory, using a long listing format `-l` and sorted by time `-t`.

```bash
ls -lt | head
```

#### List All Files Including Dotfiles

The `-a` or `--all` option will list all files, including dotfiles

```bash
ls -a
```

#### List Files Without Using `ls`

Use the Bash shell's filename expansion and brace expansion capabilities to obtain the filenames:

```bash
# display the files and directories that are in the current directory
printf "%
sn" *

# display only the directories in the current directory
printf "%
sn" */

# display only (some) image files
printf "%
sn" *.{gif,jpg,png}
```

To capture a list of files into a variable for processing, it is typically good practice to use a bash array:

```bash
files=( * )
# iterate over them
for file in "${files[@]}"; do
    echo "$file"
done
```

#### List Files in a Tree-Like Format

Use

```bash
tree github/dev117uday
```

**Output :**

```bash
├── docs
│   ├── index.md
│   └── notes
│       ├── Database
│       │   ├── mongodb.md
│       │   ├── postgresql.md
│       │   └── sqlite.md
│       ├── images
│       │   ├── git-cheat-sheet.png
│       │   ├── mockaroo.png
│       │   ├── vscode-sql-mockaroo-changes.png
│       │   └── where_clause.png
│       ├── Rust
│       │   ├── concepts_of_rust.md
│       │   ├── formating.md
│       │   ├── lifetimes.md
│       │   └── structs.md
│       ├── shell
│       │   ├── getting_started.md
│       │   ├── listing_files.md
│       │   └── navigating_directory.md
│       ├── Tools
│       │   └── git-github.md
│       └── Web
│           ├── node-express-fcc.md
│           └── react-fcc.md
├── LICENSE
├── mkdocs.yml
└── README.md

8 directories, 21 files
```

#### List Files Sorted by Size

The ls command's -S option sorts the files in descending order of file size

```bash
$ ls -l -S ./Fruits
total 444
-rw-rw-rw- 1 root root 295303 Jul 28 19:19 apples.jpg
-rw-rw-rw- 1 root root 102283 Jul 28 19:19 kiwis.jpg
-rw-rw-rw- 1 root root 50197 Jul 28 19:19 bananas.jpg
```

When used with the -r option the sort order is reversed

```bash
$ ls -l -S -r /Fruits
total 444
-rw-rw-rw- 1 root root 50197 Jul 28 19:19 bananas.jpg
-rw-rw-rw- 1 root root 102283 Jul 28 19:19 kiwis.jpg
-rw-rw-rw- 1 root root 295303 Jul 28 19:19 apples.jpg
```

## Redirection

**Redirecting standard output**

* `>` redirect the standard output (aka `STDOUT` ) of the current command into a file or another descriptor. These examples write the output of the ls command into the file `file.txt`

```
ls > file.txt
> file.txt ls
```

The target file is created if it doesn't exists, otherwise this file is truncated.

*   The default redirection descriptor is the standard output or 1 when none is specified. This command is equivalent to the previous examples with the standard output explicitly indicated:

    ```
    ls 1>file.txt
    ```

    Note: the redirection is initialized by the executed shell and not by the executed command, therefore it is done before the command execution.

#### Append vs Truncate

**Truncate >**

1. Create specified file if it does not exist.
2. Truncate (remove file's content)
3.  Write to file

    ```
    $ echo "first line" > file.txt
    $ echo "second line" > file.txt
    $ cat file.txt
    second line
    ```

    **Append >>**
4. Create specified file if it does not exist.
5. Append file (writing at end of file).

**Overwrite existing file**

```
$ echo "first line" > file.txt
```

**Append a second line**

```
$ echo "second line" >> file.txt
$ cat file.txt
first line
second line
```
