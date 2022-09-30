# Linux Commands Part 9 - 10

Tags: linux-com-book

- User accounts are defined in the `/etc/passwd` file
- groups are defined in the `/etc/group` file

![Untitled](Linux%20Commands%20Part%209%20-%2010%2039c5ef9cd69f4878b519893b9049e219/Untitled.png)

![Untitled](Linux%20Commands%20Part%209%20-%2010%2039c5ef9cd69f4878b519893b9049e219/Untitled%201.png)

![Untitled](Linux%20Commands%20Part%209%20-%2010%2039c5ef9cd69f4878b519893b9049e219/Untitled%202.png)

![Untitled](Linux%20Commands%20Part%209%20-%2010%2039c5ef9cd69f4878b519893b9049e219/Untitled%203.png)

![Untitled](Linux%20Commands%20Part%209%20-%2010%2039c5ef9cd69f4878b519893b9049e219/Untitled%204.png)

- notes of chown and chgrp

---

`d|rwx|rwx|rwx`

- d : directory
- 1st block for user
- 2nd block for group (of user)
- 3rd block for other

`chmod u=rwx [test.sh](http://test.sh/)
chmod g=rwx [test.sh](http://test.sh/)
chmod o=rwx [test.sh](http://test.sh/)
chmod go-wx [test.sh](http://test.sh/)
chmod 744 [test.sh](http://test.sh/)`

read  = 4
write = 2
exec  = 1
+ 7

`chown` : to change the file ownership
`chgrp` : to change the group

grep : -i to avoid case sensitivity

locate "file name" | grep "to filter"

tar -cf file.tar File/

- c to compress
-f for file
-x extract

Tar is an archiver, meaning it would archive multiple files into a single file but without compression. Gzip which handles the . gz extension is the compression tool that is used to reduce the disk space used by the file

add -z flag to use gzip

> : add completely new content to the file
> 
> 
> > : append new content to the file
> > 

---

## Processes

- When a system starts up, the kernel initiates a few of its own activities as processes and launches a program called init
- init, in turn, runs a series of shell scripts (located in /etc) called init scripts
- The fact that a program can launch other programs is expressed in the process scheme as a parent process producing a child process

```bash
# to look at process 
ps 

# to show all process regardless of terminal
ps x

# output 
PID TTY      STAT   TIME COMMAND
   1876 ?        Ss     0:02 /usr/lib/systemd/systemd --user
   1881 ?        S      0:00 (sd-pam)
   1895 ?        Ss     0:12 /usr/bin/appimagelauncherd
   1902 ?        Sl     0:00 /usr/bin/gnome-keyring-daemon --daemon
   1915 tty2     Ssl+   0:00 /usr/libexec/gdm-wayland-session /usr/
   1917 ?        Ss     0:00 /usr/bin/dbus-broker-launch --scope us
   1920 ?        S      0:02 dbus-broker --log 4 --controller 9 --m
   1923 tty2     Sl+    0:00 /usr/libexec/gnome-session-binary
   1982 ?        Ssl    0:00 /usr/libexec/gnome-session-ctl --monit
   1983 ?        Ssl    0:00 /usr/libexec/uresourced --user
   1986 ?        Ssl    0:00 /usr/libexec/gnome-session-binary --sy
   1990 ?        Ssl    0:00 /usr/libexec/gvfsd

# for a detailed look
ps aux

# output
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.0  0.2 173328 17748 ?        Ss   16:29   0:01 /usr/lib/systemd/systemd
root           2  0.0  0.0      0     0 ?        S    16:29   0:00 [kthreadd]
root           3  0.0  0.0      0     0 ?        I<   16:29   0:00 [rcu_gp]
root           4  0.0  0.0      0     0 ?        I<   16:29   0:00 [rcu_par_gp]
root           5  0.0  0.0      0     0 ?        I<   16:29   0:00 [netns]
root           7  0.0  0.0      0     0 ?        I<   16:29   0:00 [kworker/0:0H-events_highpri]
root           9  0.0  0.0      0     0 ?        I<   16:29   0:00 [kworker/0:1H-events_highpri]
root          10  0.0  0.0      0     0 ?        I<   16:29   0:00 [mm_percpu_wq]
root          11  0.0  0.0      0     0 ?        I    16:29   0:06 [kworker/u32:1-blkcg_punt_bio]
root          12  0.0  0.0      0     0 ?        I    16:29   0:00 [rcu_tasks_kthread]
root          13  0.0  0.0      0     0 ?        I    16:29   0:00 [rcu_tasks_rude_kthread]
root          14  0.0  0.0      0     0 ?        I    16:29   0:00 [rcu_tasks_trace_kthread]
root          15  0.0  0.0      0     0 ?        S    16:29   0:00 [ksoftirqd/0]
```

![Untitled](Linux%20Commands%20Part%209%20-%2010%2039c5ef9cd69f4878b519893b9049e219/Untitled%205.png)

**Information shown by top**

![Untitled](Linux%20Commands%20Part%209%20-%2010%2039c5ef9cd69f4878b519893b9049e219/Untitled%206.png)

![Untitled](Linux%20Commands%20Part%209%20-%2010%2039c5ef9cd69f4878b519893b9049e219/Untitled%207.png)

- to kill a process : `kill -signal [PID]`

![Untitled](Linux%20Commands%20Part%209%20-%2010%2039c5ef9cd69f4878b519893b9049e219/Untitled%208.png)

![Untitled](Linux%20Commands%20Part%209%20-%2010%2039c5ef9cd69f4878b519893b9049e219/Untitled%209.png)

![Untitled](Linux%20Commands%20Part%209%20-%2010%2039c5ef9cd69f4878b519893b9049e219/Untitled%2010.png)