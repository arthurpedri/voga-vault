![[vimcheatsheetDark.png]]

[[Vim Mnemonics (ChatGPT)]]

`f` - find after
`F`- Find before
`n` - next
`c` - cut and insert
`d` - delete
`iw` - inside word
`i"` - inside quotes (doesn't need to be above the quotes)
`aw` - word with whitespace after
`a"` - word including both quotes
`ap` - paragraph (contiguous code)
`*` - search (under cursor) 
`Ctrl+u` - page up
`Ctrl+d` - page down
**`i`** - switch to insert mode before the cursor
**`I`** - insert text at the beginning of the line
**`a`** - switch to insert mode after the cursor
**`A`** - insert text at the end of the line
**`o`** - open a new line below the current one
**`O`** - open a new line above the current one
`=` - auto indent
## Editing Text
- **`r`** – replace a single character (and return to command mode)
- **`cc`** – replace an entire line (deletes the line and moves into insert mode)
- **`C`** / **`c$`** – replace from the cursor to the end of a line
- **`cw`** – replace from the cursor to the end of a word
- **`s`** – delete a character (and move into insert mode)
- **`J`** – merge the line below to the current one with a space in between them
- **`gJ`** – merge the line below to the current one with no space in between them
- **`u`** – undo
- **`Ctrl`** + **`r`** – redo
- **`.`** – repeat last command
### Cutting, Copying And Pasting
- **`yy`** – copy (yank) entire line
- `yw` - yank word
- **`#yy`** – copy the specified number of lines
- `Ctrl + Insert` - copy in insert mode
- `Shift + Insert` - paste in insert mode
- **`dd`** – cut (delete) entire line
- **`#dd`** – cut the specified number of lines
- **`p`** – paste after the cursor
- **`P`** – paste before the cursor
## Marking Text (Visual Mode)
- **`v`** – select text using character mode
- **`V`** – select lines using line mode
- **`Ctrl`**+**`v`** – select text using block mode
-  **`o`** – move from one end of the selected text to the other
- **`aw`** – select a word
- **`ab`** – select a block with ()
- **`aB`** – select a block with {}
- **`at`** – select a block with <>
- **`ib`** – select inner block with ()
- **`iB`** – select inner block with {}
- **`it`** – select inner block with <>
### Visual Commands
- **`y`** – yank (copy) the marked text
- **`d`** – delete (cut) the marked text
- **`p`** – paste the text after the cursor
- **`u`** – change the market text to lowercase
- **`U`** – change the market text to uppercase
## Search in File
- **`*`** – jump to the next instance of the current word
- **`#`** – jump to previous instance of the current word
- **`/pattern`** – search forward for the specified pattern
- **`?pattern`** – search backward for the specified pattern
- **`n`** – repeat the search in the same direction
- **`N`** – repeat the search in the opposite direction
## Saving and Exiting File
- **`:w`** – save the file
- **`:wq`** / **`:x`** / **`ZZ`** – save and close the file
- **`:q`** – quit
- **`:q!`**/ **`ZQ`** – quit without saving changes
- **`:w new_file_name`** – save the file under a new name and continue editing the original
- **`:sav`** – save the file under a new name and continue editing the new copy
- **`:w !sudo tee %`** – write out the file using sudo and [tee command](https://phoenixnap.com/kb/linux-tee)
## Marks and Jumps
- **`m[a-z]`** – mark text using character mode (from **`a`** to **`z`**)
- **`M[a-z]`** – mark lines using line mode (from **`a`** to **`z`**)
- **`` `a ``** - jump to position marked **`a`**
- **`` `y`a ``** – yank text to position marked **>`a>`**
- **`` `. ``** – jump to last change in file
- **`` `0 ``** – jump to position where Vim was last exited
- **` `` `** – jump to last jump
- **`:marks`** – list all marks
- **`:jumps`** – list all jumps
- **`:changes`** – list all changes
- **`Ctrl+i`** – move to next instance in jump list
- **`Ctrl+o`** – move to previous instance in jump list
- **`g,`** – move to next instance in change list
- **`g;`** – move to previous instance in change list
## Macros
- **`qa`**  – record macro **`a`**
- **`q`**  – stop recording macro
- **`@a`**  – run macro **`a`**
- **`@@`**  – run last macro again