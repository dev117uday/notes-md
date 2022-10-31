# Linux Commands Part 9 - 10

Tags: linux-com-book

* User accounts are defined in the `/etc/passwd` file
* groups are defined in the `/etc/group` file

![file types](<Linux Commands Part 9 - 10 39c5ef9cd69f4878b519893b9049e219/Untitled.png>)

![permission attributes](<Linux Commands Part 9 - 10 39c5ef9cd69f4878b519893b9049e219/Untitled 1.png>)

![chmod permission symbolic notation](<Linux Commands Part 9 - 10 39c5ef9cd69f4878b519893b9049e219/Untitled 2.png>)

![chmod notation example](<Linux Commands Part 9 - 10 39c5ef9cd69f4878b519893b9049e219/Untitled 3.png>)

![file permission in octal](<Linux Commands Part 9 - 10 39c5ef9cd69f4878b519893b9049e219/Untitled 4.png>)

### chown and chgrp

* `chown` : to change the file ownership&#x20;
* `chgrp` : to change the group

`d|rwx|rwx|rwx`

* d : directory
* 1st block for user
* 2nd block for group (of user)
* 3rd block for other

```
chmod u=rwx test.sh
chmod g=rwx test.sh
chmod o=rwx test.sh
chmod go-wx test.sh
chmod 744 test.sh
```

numbering system : read = 4 write = 2 exec = 1

## Processes

* When a system starts up, the kernel initiates a few of its own activities as processes and launches a program called init
* init, in turn, runs a series of shell scripts (located in /etc) called init scripts
* The fact that a program can launch other programs is expressed in the process scheme as a parent process producing a child process

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

![process state diagram](<Linux Commands Part 9 - 10 39c5ef9cd69f4878b519893b9049e219/Untitled 5.png>)

**Information shown by top**

![top field information](<Linux Commands Part 9 - 10 39c5ef9cd69f4878b519893b9049e219/Untitled 6.png>)

![top field information](<Linux Commands Part 9 - 10 39c5ef9cd69f4878b519893b9049e219/Untitled 7.png>)

* to kill a process : `kill -signal [PID]`

![process signals](<Linux Commands Part 9 - 10 39c5ef9cd69f4878b519893b9049e219/Untitled 8.png>)

![process signals part 2](<Linux Commands Part 9 - 10 39c5ef9cd69f4878b519893b9049e219/Untitled 9.png>)

![process signals part 3](<Linux Commands Part 9 - 10 39c5ef9cd69f4878b519893b9049e219/Untitled 10.png>)
