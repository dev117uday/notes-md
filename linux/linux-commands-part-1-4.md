# Linux Commands Part 1 - 4

Tags: linux-com-book

## Introductory Commands

* `#` before terminal means super-user
* `date` to print date and time
  * `Sat Jun 18 12:01:17 AM IST 2022`
* `cal` to print calendar
* `df` to print disk drive and usage
* `free` to print memory
* `pwd` print working directory
* `Absolute PathName` : begins with root directory and follows the tree branch by branch till the desired folder
* `Relative PathName` : starts from the working directory
* `cd` to change directory
  * `cd -` to revert to previous directory
  * `cd ~username` : to change directory to another user
*   ls : to list directories

    * `ls directory_1 directory_2` : to print list or multiple directories

    ```java
    ➜  ~ ls programm software
    programm:
    azure-dev-hackathon  inbox-app            
    configs              learning-springboot  
    demo                 playground           

    software:
    jetbrains-toolbox  tor-browser_en-US
    ```

    * `ls -l` : for more details
    * `ls -lt` : to list sorted acc. date modifed
      * `—reverse` : to reverse the sort

    ![List of options of ls command](<Linux Commands Part 1 - 4 8a90b47bf4534dd9a5713b372feb6b15/Untitled.png>)

Long Listing Details

![details of fields printing long list](<Linux Commands Part 1 - 4 8a90b47bf4534dd9a5713b372feb6b15/Untitled 1.png>)

* `file filename` : to print a brief description of the file’s contents
* `less` : to view content of file

## File Structure

![Linux file structure part 1](<Linux Commands Part 1 - 4 8a90b47bf4534dd9a5713b372feb6b15/Untitled 2.png>)

![Linux file structure part 2](<Linux Commands Part 1 - 4 8a90b47bf4534dd9a5713b372feb6b15/Untitled 3.png>)

![Linux file structure part 3](<Linux Commands Part 1 - 4 8a90b47bf4534dd9a5713b372feb6b15/Untitled 4.png>)

![Linux file structure part 4](<Linux Commands Part 1 - 4 8a90b47bf4534dd9a5713b372feb6b15/Untitled 5.png>)

![Linux file structure part 5](<Linux Commands Part 1 - 4 8a90b47bf4534dd9a5713b372feb6b15/Untitled 6.png>)

## Symbolic Links | Soft Link | Symlink

* symbolic links are like aliases or another name for the file

```java
lrwxrwxrwx 1 root root
11 2018-08-11 07:34 libc.so.6 ***->*** libc-2.6.so
```

**Why they are useful ?**

* Imagine we have a file with name `foo` . Whenever we update it we, change its name to foo-date-time, but the programs/user referencing it wouldst know that the name has change. To tackle this problem, we create a symlink of file foo → foo-date-time and the programs/user user only reference the symlink.
* So even if we change the name of file foo, it wont affect the programs as they would be referencing the symlink.

## Manipulating Files and Directories

* to create new directories
  * `mkdir dir_name`
* to create multiple directories
  * `mkdir dir1 dir2 dir3`
* to copy file to another directory
  * `cp item directory`
  * if `cp item1 item2` then content of item2 is replace with item1
* use `-a` file while copying to copy the attributes as well

![options for cp command](<Linux Commands Part 1 - 4 8a90b47bf4534dd9a5713b372feb6b15/Untitled 7.png>)

* The `mv` command performs both file moving and file renaming, depending on how it is used
* to move item to another directory `mv item... directory`
* to delete item `rm item`

![options for rm command](<Linux Commands Part 1 - 4 8a90b47bf4534dd9a5713b372feb6b15/Untitled 8.png>)

## Hard Links vs Soft Links

### Hard Link

* Hard links are the original Unix way of creating links
* Every file has a single hard link that gives the file its name
* Limitations
  * A hard link cannot reference a file outside its own file system
  * A hard link may not reference a directory
* A hard link is indistinguishable from the file itself

```bash
// for hard link
-> ln file.txt link

-> ls
-rw-r--r--. 1 udayyadav udayyadav  12 Jun 20 23:06 file.txt
-rw-r--r--. 2 udayyadav udayyadav  12 Jun 20 23:06 link1
```

### Soft Link

* They work by creating a special type of file that contains a text pointer to the referenced file or directory
* They are like windows shortcuts
* If file is deleted, then link points to nothing, it is broken

```bash
// for soft link
-> ln -s file.txt link

-> ls
lrwxrwxrwx. 1 udayyadav udayyadav   9 Jun 21 07:59 link2 -> file2.txt
```

## WildCards

![different wildcards present](<Linux Commands Part 1 - 4 8a90b47bf4534dd9a5713b372feb6b15/Untitled 9.png>)

![matching with different characters](<Linux Commands Part 1 - 4 8a90b47bf4534dd9a5713b372feb6b15/Untitled 10.png>)

![wildcard example](<Linux Commands Part 1 - 4 8a90b47bf4534dd9a5713b372feb6b15/Untitled 11.png>)
