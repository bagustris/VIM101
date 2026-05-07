# VIM101 Learn Examples

Hands-on Vim exercises based on the article
[8 Vim Tips and Tricks for Experienced Users](https://itsfoss.com/pro-vim-tips/) by Sylvain Leroux.

Each example consists of:

- `<topic>.orig` — the input file fed to Vim
- `<topic>.sh`   — a Bash script that runs Vim non-interactively, applies the illustrated commands, writes `<topic>.out`, then opens `vimdiff` to compare before and after
- `<topic>.png`  — screenshot from the original article (where available)

Quit vimdiff with `:qa!`

> The article covers 8 tips. This directory contains runnable examples for 6 of them.
> Tips 7 (Inline Help) and 8 (Scripting with Ex Commands) have no example files
> since they are better explored interactively.

---

## Examples (in article order)

### 1. changing-capitalization

Input: a short copyright/disclaimer paragraph in mixed case.

Commands demonstrated:

```vim
~          " toggle case of character under cursor (normal mode)
:$norm gUU " apply gUU (uppercase whole line) to the last line via :normal
```

**Key concept:** `~`, `gu`, `gU`, and `g~` operators for case conversion; `:normal` to replay normal-mode keystrokes from the command line.

---

### 2. searching-replacing-on-steroids

Input: a paragraph from *The Adventures of Tom Sawyer*.

Commands demonstrated:

```vim
:s/black/white/                      " basic substitution (first occurrence on current line)
:s/Ben\( Rogers\)\@!/Ben Rogers/g    " replace 'Ben' not followed by ' Rogers' with 'Ben Rogers'
:s/.*/<p>\r&\r<\/p>/                 " wrap entire line in <p> tags using & (whole match) and \r (newline)
:-1s/–/\&mdash;/g                    " on previous line replace en-dash with HTML entity
```

**Key concept:** `\@!` zero-width negative lookahead; `&` in replacement for the whole match; `\r` to insert a newline in the replacement; `\( \)` grouping.

---

### 3. moving-things-around-in-no-time

Input: a "Pros/Cons" list with a typo and items in the wrong section.

Commands demonstrated:

```vim
/Power/              " search for 'Power'
ddp                  " delete line then paste below (swap with next line)
:/user-friendly/m$   " move the 'user-friendly' line to end of file
g;                   " jump back to previous change position in the change list
:/Cons/+1m-2         " move the line after 'Cons' two lines up from current position
```

**Key concept:** `:m[ove]` for non-destructive line relocation; `ddp` / `ddkP` for adjacent-line swapping; `g;` / `g,` to walk the change list.

---

### 4. applying-commands-on-an-address-range

Input: an HTML snippet containing a `<table>` with blank lines between rows.

Commands demonstrated:

```vim
:/<table>/,/<\/table>/g/^$/d   " delete blank lines inside the table
:/^$/;/^$/-1m1                 " move a blank line to just after line 1
:2,$-1>                        " indent lines 2 through second-to-last
```

**Key concept:** address ranges — `/<pat1>/,/<pat2>/` selects from one pattern match to another; `;` chains a relative offset onto the previous match.

---

### 5. piping-commands

Input: a heredoc shell script that contains unsorted month/percentage data.

Commands demonstrated:

```vim
:2,/^EOT/-1!sort -k2n -k1M         " sort lines 2 through EOT-1 by numeric col 2, then month col 1
:$r! date "+Data obtained the \%c"  " append current date/time from the shell
:1,/^EOT/!bash                      " pipe lines 1–EOT through bash to execute them
```

**Key concept:** `:{range}!{cmd}` pipes a buffer range through any shell command and replaces it with the output; `:r!` reads a command's stdout into the buffer.

---

### 6. typing-less

Input: empty file (abbreviation expansion demo).

Commands demonstrated:

```vim
:ab apple Apple Computer, Inc.   " define insert-mode abbreviation
i                                " enter insert mode; type 'apple' and it expands automatically
```

**Key concept:** `:ab[breviate]` maps a short trigger word to a longer string; expansion fires when a non-keyword character (space, punctuation, `<Esc>`) follows the trigger.

---

### 7. Inline Help System (no example file)

Vim ships with comprehensive built-in documentation accessible without leaving the editor.

```vim
:help help    " display the help overview
:help m       " show docs for the 'm' motion command
:help :m      " show docs for the :move ex command
```

**Key concept:** prefix with `:` to look up ex commands vs. bare names for normal-mode commands.

---

### 8. Scripting with Ex Commands (no example file)

Vim's `:` commands are the ex language and can be driven from a shell script for batch editing.

```bash
ex some_file << EOT
0pu_
1,/^[^#]/-1d
0r NEW.HEADER
1,.s/^/# /
wq
EOT
```

**Key concept:** any sequence of ex commands can be piped into `ex` (or `vim -e`) to automate bulk edits across files without opening an interactive session.

---

## Running an example

```bash
cd /path/to/VIM101/learn
bash changing-capitalization.sh
```

Each script is self-contained: it reads the `.orig` file, runs Vim headlessly, writes a `.out` file, then opens `vimdiff orig out` so you can inspect every change.
