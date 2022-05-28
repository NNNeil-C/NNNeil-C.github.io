---
title: Vim note
date: 2022-05-28 17:16:38
categories: common skills
tags:
- vim
---

# Vim note

## Helpful links

- A tutorial. https://danielmiessler.com/study/vim/#textobjects

## Vim configuration
### set preference on ~/.vimrc
Set all preference on ~/.vimrc. If not such a file, touch it.
Don't use `source` in your Bash shell; the right command is `:source .vimrc` **inside Vim**!

```bash
inoremap jk <ESC> # map jk as ESC
let mapleader = "'" # any shortcut after type "'"
syntax on # highlight syntax
set number # show line numbers
set noswapfile # disable the swapfile
set hlsearch # highlight all results
set ignorecase # ignore case in search
set incsearch # show search results as you type
```
## FAQ
### search
- "/whatever(forward)" or "?whatever(backward)" in command mode and press Enter
- type n to go next
- type N to go previous
### Undo & Redo
- Undo: in command mode, "u"
- Redo: in command mode, "ctrl + r"

### Save

- **`:w`**: write your changes to the file
- **`:q!`**: get out of vim (quit), but without saving your changes (!)
- **`:wq`**: write your changes and exit `vim`
- **`:saveas ~/some/path/`**: save your file to that location`vim`

### Jump to a certain character in a line
- **`f<`** #Jump forward and land on the < character (think as find)
- **`t<`**# Jump forward and land right before the < character (think as to)

### A search reference

- **`/{string}`**: search for string
- **`t`**: jump up to a character
- **`f`**: jump onto a character
- **`\*`**: search for other instances of the word under your cursor
- **`n`**: go to the next instance when you've searched for a string
- **`N`**: go to the previous instance when you've searched for a string
- **`;`**: go to the next instance when you've jumped to a character
- **`,`**: go to the previous instance when you've jumped to a character

### Clear highlight

- **`:noh`** cancel all the highlight in the screen

### Moving cursor

- **`h`** for left
- **`j`** for down
- **`k`** for up
- **`l`** for right

### Moving in line

- **`0`**: move to the beginning of the line
- **`$`**: move to the end of the line
- **`^`**: move to the first non-blank character in the line
- **`t"`**: jump to right before the next quotes
- **`f"`**: jump and land on the next quotes

### Moving by word

- **`w`**: move forward one word

- **`b`**: move back one word

- **`e`**: move to the end of your word

  #### Consider 'sth-sth' as a word(like Data-Driven)

  - **`W`**: move forward one big word
  - **`B`**: move back one big word

### Moving by stentence or paragraph

- **`)`**: move forward one sentence(a sentence is end by a ".")
- **`(`**:move backward one sentence(a sentence is end by a ".")
- **`}`**: move forward one paragrap
- **`{`**:move backward one paragrap

### Moving with screen

- **`H`**: move to the top of the screen
- **`M`**: move to the middle of the screen
- **`L`**: move to the bottom of the screen
- **`gg`**: go to the top of the file
- **`G`**: go to the bottom of the file
- **`^U`**: move up half a screen
- **`^D`**: move down half a screen
- **`^F`**: page down
- **`^B`**: page up

### Jumping back and forth

- **`Ctrl-i`**: jump to your previous navigation location
- **`Ctrl-o`**: jump back to where you were

### Other motions

- **`:$line_numberH`**: move to a given line number
- **`^E`**: scroll up one line
- **`^Y`**: scroll down one line
- **`^U`**: move up half a page
- **`^D`**: move down half a page
- **`^F`**: move down a page
- **`^B`**: move up a page

### About Modes

![vim_modes](/Users/chenzifeng/Downloads/vim_modes.png)

### Basic Changing Text

Let's start with the options here.

- **`i`**: *insert* before the cursor
- **`a`**: *append* after the cursor
- **`I`**: *insert* at the beginning of the line
- **`A`**: *append* at the end of the line
- **`o`**: *open* a new line below the current one
- **`O`**: *open* a new line above the current one
- **`r`**: *replace* the one character under your cursorø**`R`**: *replace* the character under your cursor, but just keep typing afterwards
- **`cm`**: change whatever you define as a *movement*, e.g. a word, or a sentence, or a paragraph.ø
- **`C`**: *change* the current line from where you're at (delete after the cursor)
- **`ct?`**: *change* change up to the question mark
- **`s`**: *substitute* from where you are to the next command (noun)
- **`S`**: *substitute* the entire current line (delete the whole line)

### Chaing Case

- **`~`**: change case under the cursor or selection

### Formatting Text

- **`gq ap`**: format the current paragraph

### Basic deletion options

- **`x`**: *exterminate* (delete) the character under the cursor
- **`X`**: *exterminate* (delete) the character before the cursor
- **`dm`**: delete whatever you define as a *movement*, e.g. a word, or a sentence, or a paragraph.
- **`dd`**: *delete* the current line
- **`dt.`**: *delete* delete from where you are to the period
- **`D`**: *delete* to the end of the line
- **`J`**: *join* the current line with the next one (delete what's between)

### Use command "." to repeat actions

- delete a word  **dw**

- delete five more words  **5.**
- **It won't repeat itself**

### Copy and Paste

#### Simple Copy

- **`y`**: yank (copy) whatever's selected
- **`yy`**: yank the current line

#### Simple Cut

- as same as Deleting

#### Simple Pasting

- **`p`**: paste the copied (or deleted) text after the current cursor position
- **`P`**: paste the copied (or deleted) text before the current cursor position

#### Switching lines of text

- **ddp**

  This is a quick trick you can use to swap the position of two lines of text. The first part deletes the line you're on, and the second part puts it back above where it used to be.

### Spellcheck

- **`set spell spelllang=en_us`** in the ~/.vimrc
- **`]s`**: go to the next misspelled word
- **`[s`**: go to the previous misspelled word
- **`z=`**: get some suggestions
- **`zg`**: mark a word as correct
- **`zw`**: mark a word as misspelled

### Simple Replacement(Substitution)

#### change "foo" to "bar" on every lin

- **`:%s /foo/bar/g`**

#### change "foo" to "bar" on just the current line

- **`:s /foo/bar/g`** 

### Some Object reference

- **words**: `iw` and `aw`
- **sentences**: `is` and `as`
- **paragraphs**: `ip` and `ap`
- **single quotes**: `i'` and `a'`
- **double quotes**: `i"` and `a"`
- **back ticks**: ``i` `` and ``a` ``
- **parenthesis**: `i(` and `a(`
- **brackets**: `i[` and `a[`
- **braces**: `i{` and `a{`
- **tags**: `it` and `at`



### Visual Mode

### how to enter visual mode

- **character-based**: `v`
- **line-based**: `V`
- **column-based**: `Ctrl-v`

#### some tricks on selection

- **`vi(`**: select in side of parenthesis (also work for ", . ( { [")
- **`v2i{`**:  select everything inside the second tier braces
- **`ggVG`**: select all

#### Prepend anything to multiple lines

1. Press Esc to enter 'command mode'
2. Use Ctrl + V to enter visual block mode.
3. Move Up / Down to select the columns of text in the lines you want to comment.
4. Then hit Shift + i and type the text you want to insert.
5. Then hit Esc , wait 1 second and the inserted text will appear on every line.



### Changing file type

- **`set ft=sometype`**
