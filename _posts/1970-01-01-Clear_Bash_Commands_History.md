---
layout: post
title: Clear Bash Commands History
categories: Linux
---

### Quit Bash Shell Without Saving Current History

1. Clear current history stored in RAM and then exit:
```
history -c && exit
```

2. Unset HISTFILE then exit:
```
unset HISTFILE
exit
```

3. Terminate current bash process:
```
kill -9 $$
```

If you want make these commands more permanent then these commands could be added on ~/.bash_logout file or used with aliases.

### Clear Bash History Completely

1. Remove ~./bash_history file, then clear current history and exit:
```
rm -rf ~/.bash_history
history -c && exit
```

2. Set HISTSIZE to 0 (zero) then exit:
```
HISTSIZE=0 && exit
```


### Send .bash_history to a black hole:
```
rm -rf ~/.bash_history
ln -s /dev/null ~/.bash_history
```

See also:
[Quit Bash Shell Without Saving Bash History (5 Methods)](https://www.if-not-true-then-false.com/2010/quit-bash-shell-without-saving-bash-history/)
[DISABLING BASH_HISTORY AND/OR LOGGING ALL USER'S CMDS](http://mewbies.com/how_to_disable_bash_history_or_limit_tutorial.html)
