---
layout: post
title: Clear Bash Commands History
categories: Linux
---

Once you have logged out of your shell by default bash will store the last commands in 1000 lines, you executed to your .bash_history file for easy recall on future sessions, even passwords that were entered as plain text.


### Quit bash shell without saving current history

* Clear current history stored in RAM and then exit:

    history -c && exit

* Unset HISTFILE then exit:

    unset HISTFILE
    exit

* Terminate current bash process:

    kill -9 $$

If you want make these commands more permanent then these commands could be added on ~/.bash_logout file or used with aliases.

### Clear bash history completely

* Remove ~./bash_history file, then clear current history and exit:

    rm -rf ~/.bash_history
    history -c && exit

### Send .bash_history to a black hole

    rm -rf ~/.bash_history
    ln -s /dev/null ~/.bash_history

See also:

[Quit Bash Shell Without Saving Bash History (5 Methods)](https://www.if-not-true-then-false.com/2010/quit-bash-shell-without-saving-bash-history/)

[DISABLING BASH_HISTORY AND/OR LOGGING ALL USER'S CMDS](http://mewbies.com/how_to_disable_bash_history_or_limit_tutorial.html)
