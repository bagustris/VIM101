# vimcheat.sh: the vim cheatsheet
Usage:  
$ less `vimcheat.sh` then `/typewhatyoulookfor`  
:command <space> arguments <space> Explanation: for command inside VIM OR  
shortcut <space> Explanation: for shortcut, eg: ciw (C+I+W) to change inner word  
`:set ...` can be writtent in .vimrc instead of command
 
## Basics
`:w`	Save file  
`:q`	Exit Vim  
`:wq`   Save and Exit  
`:q!`	Quit without saving  
`:x`	Write file (if changes has been made) and exit  
`:r filename`     Read filename  
`:saveas filename`	Saves file as filename (same as :wq filename OR :sav filename)  
`$vim +linenumber file` open file on linenumber
`$vim '+normal Go' file` open file and insert last line (Go)
`.`     Repeats the last change made in normal mode  
`5.`    Repeats 5 times the last change made in normal mode  

## Moving in the file
`k` 	move the cursor up one line  
`j` 	move the cursor down one line  
`w`     move the cursor to beginning of next WORD
`e`	    move the cursor to the END of the word  
`b`	    move the cursor to the BEGINNING of the word/previous word  
`0`	    move the cursor to the begining of the LINE  
`G`	    move the cursor to the end of the file
`gg`	move the cursor to the begining of the file
`Shift-g` move to the end of file
`L`	    move the cursor to the bottom of the screen  
`:59`	move cursor to line 59. Replace 59 by the desired line number.  
`20|`	move cursor to column 20.  
`%`	    Move cursor to matching parenthesis  
`[[`	Jump to function start  
`[{`	Jump to block start  
`$`	    move to the end of line  
`Ctrl-O`    goes back
`Ctrl-I`    goes forward
`'"`        goes to last edit

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
`:e .` open integrated file explorer  
`:e Space Ctrl-D` or `:e tab` show file to be open  
`:e filename` Edit filename in current window  
`:Sex` Split window and open integrated file explorer  
`:ls` List buffers  
`:cd ..` Move to parent directory  
`:args` List files  
`:args *.php` Open file list  
`:grep expression *.php` Returns a list of .php files contening expression  
`gf` Open file name under cursor  
`:b#` Goes back to previously edited buffer, after `:e`
`tabe filename` open filename in new tab
`tabn` same as `gt`, next window

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
`:vsplit file` Split window vertically  
`:sview file` Same as :split in readonly mode  
`:hide` Close current window  
`:only` Close all windows, excepted current  
`:b 2` Open #2 in this window  
`:new abc.txt` edit abc.txt in new window  

## Auto-completion
`Ctrl+n Ctrl+p` (in insert mode) Complete word  
`Ctrl+x Ctrl+l` Complete line  
`Ctrl+x Ctrl+k` Complete with dictionnary  
`Ctrl+x Ctrl+f` Complete filename/omni completion  

## Insert
`i` insert text in current cursor  
`a` insert text after current cursor  
`A` insert text in the end of line  
`o` insert text below current line  
`O` insert text above current line  

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
`d%` cut block, inside {...}
`D` Cut to end of line  
`y$` Copy to end of Line  
`v0y` Copy from cursor to end of cursor (visually)  
`u`	undo  
`U`	Return the last line which was modified into original state  
`Ctrl+R`	redo  

## Search
`/word`	Search word from top to bottom  (press `n` for next word, `Shift-n` for previous word)
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
 - Put the cursor on foo.  
 - Press * to search for the next occurrence.  
 - Type ciw (change inner word) then bar then press Escape.  
 - Press n (move to next occurrence) then .  
 
Cut/copy-paste interactively (Visual Mode):  
 - press v to begin,  
 - pres V (capital V) to select whole line, Ctrl-v/Ctrl-q to select block  
 - move cursor by pressing arrow key 
 - press d to cut, or y to copy  
 - press p to paste after current line
 
## Comment
- press Esc/Ctrl-c (to leave editing or other mode)
- hit ctrl+v (visual block mode)
- use the up/down arrow keys to select lines you want (it won't highlight everything - it's OK!)
- Shift+i (capital I)
- insert the text you want, i.e. #
- press EscEsc

## Uncomment
- press Esc/Ctrl-c (to leave editing or other mode)
- hit ctrl+v (visual block mode)
- use the ↑/↓ arrow keys to select the lines to uncomment.
- If you want to select multiple characters, use one or combine these methods:
    use the left/right arrow keys to select more text, 
    to select chunks of text use shift + ←/→ arrow key, 
    you can repeatedly push the delete keys below, like a regular delete button,
    press d or x to delete characters, repeatedly if necessary.
