# vimcheat.sh: the vim cheatsheet
Ref: https://www.catswhocode.com/blog/vim-cheat-sheet-for-2016  
Usage: less `vimcheat.sh` then `/typewhatyoulookfor`  
:command arguments Explanation for command inside VIM OR  
shortcut Explanation for shortcut, eg: ciw (C+I+W) to change inner word  

## Basics
`:w`	Save file  
`:q`	Exit Vim  
`:wq`   Save and Exit  
`:q!`	Quit without saving  
`:x`	Write file (if changes has been made) and exit  
`:r filename`     Read filename  
`:sav  filename`	Saves file as filename  
`.`     Repeats the last change made in normal mode  
`5.`    Repeats 5 times the last change made in normal mode  
`$vim +linenumber` file	open file on linenumber  

## Moving in the file
`k` 	move the cursor up one line  
`j` 	move the cursor down one line  
`e`	    move the cursor to the end of the word  
`b`	    move the cursor to the begining of the word  
`0`	    move the cursor to the begining of the line  
`G`	    move the cursor to the end of the file  
`gg`	move the cursor to the begining of the file  
`L`	    move the cursor to the bottom of the screen  
`:59`	move cursor to line 59. Replace 59 by the desired line number.  
`20|`	move cursor to column 20.  
`%`	    Move cursor to matching parenthesis  
`[[`	Jump to function start  
`[{`	Jump to block start  
`$`	    move to the end of line  

## Set Leter/Case
`:set ignorecase` ignore cases in searches  
`:set smartcase` Ignore case in searches excepted if an uppercase letter is used  
`:%s/\<./\u&/g` Sets first letter of each word to uppercase  
`:%s/\<./\l&/g` Sets first letter of each word to lowercase  
`:%s/.*/\u&` Sets first letter of each line to uppercase  
`:%s/.*/\l&` Sets first letter of each line to lowercase  

## Read/Write files
`:1,10 w outfile` Saves lines 1 to 10 in outfile  
`:1,10 w >> outfile` Appends lines 1 to 10 to outfile  
`:r infile` Insert the content of infile  
`:23r infile` Insert the content of infile under line 23  

## File explorer
`:e Space Ctrl-D` Open integrated file explorer  
`:e filename` Edit filename in current window  
`:Sex` Split window and open integrated file explorer  
`:ls` List buffers  
`:cd ..` Move to parent directory  
`:args` List files  
`:args *.php` Open file list  
`:grep expression *.php` Returns a list of .php files contening expression  
`gf` Open file name under cursor  

## Interact with Unix
`:!pwd`     Execute the pwd unix command, then returns to Vi  
`!!pwd`     Execute the pwd unix command and insert output in file  
`:sh`       Temporary returns to Unix  
`$exit`     Returns to ViM  
`:!command %`   Run the command on edited file  

## Window splitting
`:split filename` Split the window and open filename  
`ctrl-w` up arrow Puts cursor in top window  
`ctrl-w` ctrl-w Puts cursor in next window  
`ctrl-w_` Maximise current window  
`ctrl-w=` Gives the same size to all windows  
`10 ctrl-w+` Add 10 lines to current window  
`:vsplit` file Split window vertically  
`:sview` file Same as :split in readonly mode  
`:hide` Close current window  
`:only` Close all windows, excepted current  
`:b 2` Open #2 in this window  
`:new abc.txt edit abc.txt in new window  

## Auto-completion
`Ctrl+n Ctrl+p` (in insert mode) Complete word  
`Ctrl+x Ctrl+l` Complete line  
`Ctrl+x Ctrl+k` Complete with dictionnary  
`Ctrl+x Ctrl+f` Complete filename/omni completion  

## Tabs
Use terminal tab instead of vim tab or splitting mode  

## Marks
Use visual mode instead  

## Text indent
`:set autoindent` Turn on auto-indent  
`:set smartindent` Turn on intelligent auto-indent  
`:set shiftwidth=4` Defines 4 spaces as indent size  
`ctrl-t, ctrl-d` Indent/un-indent in insert mode  
`>>` Indent  
`<<` Un-indent  
`=%` indent the code between parenthesis  

## Syntax highlighting
`:syntax on` Turn on syntax highlighting  
`:syntax off` Turn off syntax highlighting  
`:set syntax=perl` Force syntax highlighting  

# Copy Paste
`y` Copy word in the cursor  
`yy` Copy/yank line  
`3yy` copy 3lines  
`yw` Yank word  
`p` paste word  
`dd` Delete current line  
`D` Cut to end of line  
`y$` Copy to end of Line  
`v0y` Copy from cursor to end of cursor (visually)  
`u`	undo  
`U`	Return the last line which was modified into original state  
`Ctrl+R`	redo  

## Search
`/word`	Search word from top to bottom  
`?word`	Search word from bottom to top  
`\*`	Search the word under cursor  
`/\cstring`	Search STRING or string, case insensitive  
`/jo[ha]n`	Search john or joan  
`/\< the`	Search the, theatre or then  
`/the\>`	Search the or breathe  
`:bufdo /searchstr/`	Search in all open files  
`bufdo %s/something/somethingelse/g`	Search something in all the open buffers and replace it with somethingelse  

## Replace
`:%s/foo/bar/g` 	find all "foo" replace with bar  
`:s/foo/bar/f`	find foo with bar in current line  
`:%s/foo/bar/gc`	find-replace with confirmation  
`:%s/onward/forward/gi`	Replace onward by forward, case unsensitive   
`:%s/old/new/gc	Replace` all occurences with confirmation  
`cw` change word  
`ciw` change inner word:  
    1. Put the cursor on foo.  
    2. Press * to search for the next occurrence.  
    3. Type ciw (change inner word) then bar then press Escape.  
    4. Press n (move to next occurrence) then .  

Cut/copy-paste interacively:  
    1. press v to begin,  
    2. V to select whole line, Ctrl-v/Ctrl-q to select block  
    3. move cursor by pressing arrow key  
    4. press d to cut, or y to copy  
