---
layout: default
title: Vim Tutorial
category: Vim
---

**IMPORTANT**

The best way to find out helpful materials is to access [documentation hosted on the official website](http://www.vim.org/docs.php).
The following is for personal use, I do not guarantee the accuracy, integrity and authority. 

### Help Files

- [Vim Tutor](http://vimhelp.appspot.com/usr_01.txt.html#vimtutor)
- [Help Overview](http://vimhelp.appspot.com/)
- [Translations](http://vimcdoc.sourceforge.net/)

### Books

- *Vi IMproved - Vim*, by Steve Oualline
- *Practical Vim 2nd ed.*, by Drew Neil

See also:

- [http://iccf-holland.org/click5.html](http://iccf-holland.org/click5.html)

### Game

- [Vim Adventure](https://vim-adventures.com/)

### Vim Tutor

#### 1.1 STARTING VIM

To start Vim from the shell prompt, type:  

    vim FILENAME <ENTER>

#### 1.2 MOVING THE CURSOR

The cursor is moved using the hjkl keys.

    h (left)	j (down)       k (up)	    l (right)

#### 1.3 TEXT EDITING

To delete the character at the cursor, type:

    x

To insert text before the cursor, type: 

    i text <ESC>

To append text after the line, type:

    A text <ESC>

#### 1.4 EDITING A FILE AND EXITING VIM

To trash all changes and exit, type:

    <ESC> :q! <ENTER>

To save the changes and exit, type:

    <ESC> :wq <ENTER>

NOTE: Pressing `<ESC>` will place you in Normal mode or will cancel an unwanted and partially completed command.

#### 2.1 DELETION COMMANDS

To delete from the cursor up to the next word, type:

    dw

To delete from the cursor to the end of a line, type:

    d$

To delete a whole line, type:

    dd

#### 2.2 ON OPERATORS AND MOTIONS

To repeat a motion prepend it with a number:

    operator [number] motion

where:

- operator - is what to do, such as  d  for delete
- [number] - is an optional count to repeat the motion  
- motion   - moves over the text to operate on, such as  w (word), $ (to the end of line), etc.

A short list of motions:

- w - until the start of the next word, EXCLUDING its first character.
- e - to the end of the current word, INCLUDING the last character.
- $ - to the end of the line, INCLUDING the last character.
- 0 - (zero) to the start of the line.

NOTE: Pressing just the motion while in Normal mode without an operator will move the cursor as specified.

#### 2.3 THE UNDO COMMAND

To undo previous actions, type:

    u  (lowercase u)

To undo all the changes on a line, type:

    U  (capital U)

To undo the undo's, type:

    CTRL-R

#### 3.1 THE PUT COMMAND

To put back text that has just been deleted, type:

    p  

This puts the deleted text AFTER the cursor (if a line was deleted it will go on the line below the cursor).

#### 3.2 THE REPLACE COMMAND

To replace the character under the cursor, type:

    r

and then the character you want to have there.

#### 3.3 THE CHANGE OPERATOR

The change operator allows you to change from the cursor to where the motion takes you.
e.g. Type `ce` to change from the cursor to the end of the word, `c$` to change to the end of a line.

Notice that `ce` deletes the word and places you in Insert mode.

#### 3.4 MORE CHANGES USING c
 
The format for change is:

    c [number] motion

NOTE: You can use the Backspace key to correct mistakes while typing.

#### 4.1 CURSOR LOCATION AND FILE STATUS

- `CTRL-G`	displays your location in the file and the file status.
- `G`		moves to the end of the file.
- `number G`	moves to that line number.
- `gg`		moves to the first line.

NOTE: You may see the cursor position in the lower right corner of the screen. This happens when the 'ruler' option is set (see `:help 'ruler'`)

#### 4.2 THE SEARCH COMMAND

- Typing `/` followed by a phrase searches FORWARD for the phrase.
- Typing `?` followed by a phrase searches BACKWARD for the phrase.
- After a search type `n` to find the next occurrence in the same direction or `N` to search in the opposite direction.
- `CTRL-O` takes you back to older positions, `CTRL-I` to newer positions.

NOTE: When the search reaches the end of the file it will continue at the start, unless the 'wrapscan' option has been reset.

#### 4.3 MATCHING PARENTHESES SEARCH

Typing `%` while the cursor is on a (,),[,],{, or } goes to its match.

NOTE: This is very useful in debugging a program with unmatched parentheses!

#### 4.4 THE SUBSTITUTE COMMAND

- To substitute new for the first old in a line, type	`:s/old/new`
- To substitute new for all 'old's on a line, type	`s/old/new/g`
- To substitute phrases between two line #'s, type	`#,#s/old/new/g`
- To substitute all occurrences in the file, type	`%s/old/new/g`
- To ask for confirmation each time add 'c'	   	`%s/old/new/gc`

#### 5.1 HOW TO EXECUTE AN EXTERNAL COMMAND

`:!command` executes an external command.

Some useful examples are:

    (MS-DOS)		(Unix)
     :!dir		 :!ls			-  shows a directory listing.
     :!del FILENAME	 :!rm FILENAME		-  removes file FILENAME.

NOTE: All `:` commands must be finished by hitting `<ENTER>`. From here on we will not always mention it.

#### 5.2 MORE ON WRITING FILES

`:w FILENAME` writes the current Vim file to disk with name FILENAME.

#### 5.3 SELECTING TEXT TO WRITE

`v` motion `:w FILENAME` saves the Visually selected lines in file FILENAME.

NOTE: Pressing `v` starts Visual selection. You can move the cursor around to make the selection bigger or smaller. Then you can use an operator to do something with the text.  For example, `d` deletes the text.

#### 5.4 RETRIEVING AND MERGING FILES

- `:r FILENAME` retrieves disk file FILENAME and puts it below the cursor position.
- `:r !dir` reads the output of the dir command and puts it below the cursor position.

#### 6.1 THE OPEN COMMAND

- Type `o` to open a line BELOW the cursor and start Insert mode.
- Type `O` to open a line ABOVE the cursor.

#### 6.2 THE APPEND COMMAND

- Type `a` to insert text AFTER the cursor.
- Type `A` to insert text after the end of the line.

NOTE: `a`, `i` and `A` all go to the same Insert mode, the only difference is where the characters are inserted.

#### 6.3 ANOTHER WAY TO REPLACE

Typing a capital `R` enters Replace mode until `<ESC>` is pressed.

NOTE: Replace mode is like Insert mode, but every typed character deletes an existing character.

#### 6.4 COPY AND PASTE TEXT

The `y` operator yanks (copies) text, `p` puts (pastes) it.

NOTE: you can also use `y` as an operator; `yw` yanks one word.

#### 6.5 SET OPTION - Set an option so a search or substitute ignores case

Typing `:set xxx` sets the option "xxx". Some options are:

- 'ic' 'ignorecase'	ignore upper/lower case when searching
- 'is' 'incsearch'	show partial matches for a search phrase
- 'hls' 'hlsearch'	highlight all matching phrases

You can either use the long or the short option name.
Prepend "no" to switch an option off, e.g. `:set noic`, `:nohlsearch` 

NOTE: If you want to ignore case for just one search command, use "\c" in the phrase: `/ignore\c <ENTER>`

#### 7.1 GETTING HELP - Use the on-line help system

1. Type `:help` or press `<F1>` or `<Help>` to open a help window.
2. Type `:help cmd` to find help on "cmd".
3. Type `CTRL-W CTRL-W` to jump to another window.
4. Type `:q` to close the help window.

#### 7.2 CREATE A STARTUP SCRIPT - Enable Vim features

Vim has many more features than Vi, but most of them are disabled by default. To start using more features you have to create a "vimrc" file.

Step1 - Start editing the "vimrc" file. This depends on your system:

    :e ~/.vimrc			(for Unix)
    :e $VIM/_vimrc		(for MS-Windows)

Step 2 - Now read the example "vimrc" file contents:

    :r $VIMRUNTIME/vimrc_example.vim

Step 3 - Write the file with:

    :w

The next time you start Vim it will use syntax highlighting. You can add all your preferred settings to this "vimrc" file. For more information type `:help vimrc-intro`

#### 7.3 COMMAND LINE COMPLETION

Make sure Vim is not in compatible mode: `:set nocp`
When typing a `:` command, press `CTRL-D` to see possible completions. Press `<TAB>` to use one completion. 

