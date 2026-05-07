# vimcheat.md: the vim cheatsheet
Usage:  
$ less vimcheat.md then `/typewhatyoulookfor`  
:command <space> arguments <space> Explanation: for command inside VIM OR  
shortcut <space> Explanation: for shortcut, eg: ciw (C+I+W) to change inner word  
`:set ...` can be written in .vimrc instead of command

## Opening
`vim +L filename` open vim at line L  
`vim '+normal Go' file` open file and insert last line (Go)
 
## Basics
`:w`	Save file  
`:q`	Exit Vim  
`:wq`   Save and Exit  
`:q!`	Quit without saving  
`:x`	Write file (if changes has been made) and exit  
`:r filename`     Read filename  
`:saveas filename`	Saves file as filename (same as :wq filename OR :sav filename)  
`.`     Repeats the last change made in normal mode  
`5.`    Repeats 5 times the last change made in normal mode  

## Moving in the file
`k` 	move the cursor up one line  
`j` 	move the cursor down one line  
`w`     move the cursor to beginning of next word (keyword-word: letters, digits, `_`)  
`W`     move to beginning of next WORD (whitespace-delimited)  
`e`	    move the cursor to the END of the word  
`b`	    move the cursor to the BEGINNING of the word/previous word (keyword-word)  
`B`     move to the BEGINNING of the previous WORD (whitespace-delimited)  
`0`	    move the cursor to the beginning of the line  
`$`	    move to the end of line  
`G`	    move the cursor to the end of the file  
`gg`	move the cursor to the beginning of the file  
`L`	    move the cursor to the bottom of the screen  
`:59`	move cursor to line 59. Replace 59 by the desired line number.  
`20|`	move cursor to column 20.  
`%`	    Move cursor to matching parenthesis  
`[[`	Jump to function start  
`[{`	Jump to block start  
`Ctrl-O`    goes back  
`Ctrl-I`    goes forward  
`'.`        goes to last edit

## Set Letter/Case
`:set ignorecase` ignore cases in searches  
`:set smartcase` Ignore case in searches except if an uppercase letter is used  
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
`:tabe filename` open filename in new tab  
`:tabn` same as `gt`, next tab
`:tabp` same as `gT`, previous tab

## Interact with Unix
`:!pwd`     Execute the pwd unix command, then returns to Vi  
`!!pwd`     Execute the pwd unix command and insert output in file  
`:sh`       Temporary returns to Unix  
`exit`      Returns to Vim  
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

## Auto-completion (without plugin, only ctags)
`Ctrl+n Ctrl+p` (in insert mode) Complete word  
`Ctrl+x Ctrl+l` Complete line  
`Ctrl+x Ctrl+k` Complete with dictionnary  
`Ctrl+x Ctrl+f` Complete filename/omni path completion  
`ctrl-n` Accept suggestion

## Insert/Edit
`i` insert text before cursor  
`a` insert text after cursor  
`A` insert text at end of line  
`o` insert text below current line  
`O` insert text above current line  
`:pu=strftime('%Y-%m-%d')` insert date (eq. '%F')  
`gq{motion}` reformat/reflow text to textwidth; `gqq` for current line

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
`:set syntax=python` Force syntax highlighting  

## Copy Paste
`y{motion}` Yank (copy) over motion, e.g. `yw` yank word, `y$` yank to end of line  
`yy` Copy/yank line  
`3yy` copy 3 lines  
`p` paste after cursor (or below current line for linewise)  
`dd` Delete (cut) current line  
`d%` cut block, inside {...}  
`D` Cut to end of line  
`y$` Copy to end of line  
`v0y` Copy from cursor to beginning of line (visually)  
`u`	undo  
`U`	Return the last line which was modified into original state  
`Ctrl+R`	redo  

## Registers
`:reg`          List all register contents  
`"ay{motion}`   Yank into register a (a–z)  
`"ap`           Paste from register a  
`"+y`           Yank to system clipboard  
`"+p`           Paste from system clipboard  
`"0p`           Paste last yank (even after a delete)  
`"_dd`          Delete into black-hole register (no yank side-effect)  

## Marks
`ma`        Set mark a at current cursor position (a–z local, A–Z global)  
`` `a ``    Jump to exact position of mark a (line and column)  
`'a`        Jump to the line of mark a (first non-blank character)  
`:marks`    List all marks  
`` `. ``    Jump to position of last change (same as `'.` for line)  
`''`        Jump back to position before last jump  

## Macros
`q{reg}`    Start recording macro into register (a–z); `q` again to stop  
`@{reg}`    Replay macro from register  
`@@`        Repeat last played macro  
`5@a`       Replay macro in register a five times  
`"ap`       Inspect macro: paste register a as text to review/edit  

## Search
`/word`	Search word from top to bottom  (press `n` for next word, `Shift-n` for previous word)
`?word`	Search word from bottom to top  
`*`	Search the word under cursor  
`/\cstring`	Search STRING or string, case insensitive  
`/jo[ha]n`	Search john or joan  
`/\<the`	Search the, theatre or then (word starts with "the")  
`/the\>`	Search the or breathe (word ends with "the")  
`:bufdo /searchstr/`	Search in all open files  
`:bufdo %s/something/somethingelse/g`	Search something in all the open buffers and replace it with somethingelse  
`:noh` clear search highlight until next

## Global command
`:g/pattern/cmd`        Run ex command on every line matching pattern  
`:g!/pattern/cmd`       Run ex command on every line NOT matching pattern (same as `:v/`)  
`:g/^$/d`               Delete all blank lines  
`:g/pattern/d`          Delete all lines containing pattern  
`:g/pattern/p`          Print all lines containing pattern (like grep)  
`:g/pattern/m$`         Move all matching lines to end of file  
`:g/pattern/normal @a`  Run macro a on every matching line  

## Replace
`:%s/foo/bar/g` 	find all "foo" replace with bar  
`:s/foo/bar/`	find first foo and replace with bar in current line  
`:%s/foo/bar/gc`	find-replace with confirmation  
`:%s/onward/forward/gi`	Replace onward by forward, case insensitive  
`:%s/old/new/gc`	Replace all occurrences with confirmation  
`cw` change word  
`ciw` change inner word:  
 - Put the cursor on foo.  
 - Press * to search for the next occurrence.  
 - Type ciw (change inner word) then bar then press Escape.  
 - Press n (move to next occurrence) then .  
 
Cut/copy-paste interactively (Visual Mode):  
 - press v to begin,  
 - press V (capital V) to select whole line, Ctrl-v/Ctrl-q to select block  
 - move cursor by pressing arrow key 
 - press d to cut, or y to copy  
 - press p to paste after current line
 
## Folds
`za`        Toggle fold open/closed under cursor  
`zo`        Open fold under cursor  
`zc`        Close fold under cursor  
`zR`        Open all folds in file  
`zM`        Close all folds in file  
`zf{motion}` Manually create a fold over motion  
`zd`        Delete fold under cursor  
`:set foldmethod=indent` Fold by indentation (also: syntax, marker, expr)  

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
