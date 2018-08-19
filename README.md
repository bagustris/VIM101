# VIM101

This my repository to learn and configure VIM. 
This repitory consist of 3 parts:

1. Learn VIM

2. VIM cheatsheet

3. VIM config

## Learn VIM
1. VIMtutor
First, you should install vim and vim-runtim. In Ubuntu,

```
$ sudo apt install vim vim-runtime
$ vimtutor
```
Follow the steps there, repeat until you master it.

2. Pro-VIM-Tips
This Example from Yes, I Know IT / It's FOSS article
https://itsfoss.com/?p=14419

Each example come with the original text (.orig) and a Bash 
script (.sh) invoking Vim with the command illustrated in
the article.

After processing, the script launches `vimdiff` to compare
before/after files.

You can quit vimdiff using `:qa!`

## VIM cheatsheet
There are two cheatsheet available in the `cheatsheet` directory:
1. vim-cheatsheet.md
2. vim-cheat-sheet-en.pdf

## VIM config
In the directory `config`, there is a `.vimrc` file that I used to configure my VIM. 
Mostly I works on python, Latex and Octave, therefor the config is intended to 
optimize those languages. I modify these `.vimrc` file from `fisa-vim-config` repository.
The detail is given in the directory.