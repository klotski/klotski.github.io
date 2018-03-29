---
layout: default
title: Clear Bash Commands History
category: Linux
---

Once you have logged out of your shell by default bash will store the last commands in 1000 lines, you executed to your *.bash_history* file for easy recall on future sessions, even passwords that were entered as plain text.

### Quit bash shell without saving current history

Methond 1 - Clear current history stored in RAM and then exit

```shell
history -c && exit
```

Methond 2 - Unset HISTFILE then exit

```shell
unset HISTFILE
exit
```

Methond 3 - Terminate current bash process

```bash
kill -9 $$
```

If you want make these commands more permanent then these commands could be added on *~/.bash_logout* file or used with aliases.

### Clear bash history completely

Set HISTSIZE to 0 (zero) (It works for CentOS 6.9 but not for CentOS 7.3)

```sh
HISTSIZE=0
exit
```
Set HISTFILESIZE to 0 (zero)

```sh
HISTFILESIZE=0
exit
```

Remove *~./bash_history* file, then clear current history and exit

```sh
rm -rf ~/.bash_history
history -c && exit
```

### Send *.bash_history* to a black hole

Remove *.bash_history* file, then create a soft link redirecting to /dev/null.

```shell
rm -rf ~/.bash_history
ln -s /dev/null ~/.bash_history
```

**References:**
- [Quit Bash Shell Without Saving Bash History (5 Methods)](https://www.if-not-true-then-false.com/2010/quit-bash-shell-without-saving-bash-history/)
- [Disabling Bash_History and/or Logging All User's CMDS](http://mewbies.com/how_to_disable_bash_history_or_limit_tutorial.html)
