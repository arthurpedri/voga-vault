### Basic Movements

- **`h`**: Left (Think: **h** as in **h**ome — the starting point)
- **`j`**: Down (Imagine **j** looking like a down arrow or **j**umping down)
- **`k`**: Up (Think of **k** as a kind of up arrow, or as the "inverse" of **j**)
- **`l`**: Right (Think: **l** as in **l**ast — moving to the end)

### Words and Lines

- **`w`**: Next **w**ord
- **`e`**: End of the current **e**nd of the word
- **`b`**: **B**eginning of the previous word (think: "back")

### Paragraphs and Sentences

- **`{`**: Move to the previous paragraph (curly braces look a bit like paragraphs)
- **`}`**: Move to the next paragraph
- **`(`**: Move to the beginning of the previous sentence
- **`)`**: Move to the beginning of the next sentence

### File Navigation

- **`gg`**: **G**o to the **g**round (top) of the file
- **`G`**: Go to the **G**round (bottom) of the file

### Inserting Text

- **`i`**: **I**nsert before cursor
- **`a`**: Insert **a**fter cursor
- **`I`**: Insert at the start of the line (**I**nitial position)
- **`A`**: Insert at the **A**fter the line (end)

### Deleting Text

- **`x`**: Delete the character under the cursor (imagine "x-ing" it out)
- **`d` + motion**: **D**elete to position of motion (e.g., **dw** for **d**elete **w**ord)
- **`dd`**: **D**elete the entire line (double **d**)

### Yank (Copy) and Paste

- **`y` + motion**: **Y**ank (copy) the text in the motion (e.g., **yw** for **y**ank **w**ord)
- **`yy`**: Yank the entire line (think "double y" as duplicating the line)
- **`p`**: **P**aste after the cursor (similar to "put")
- **`P`**: Paste **P**rior to the cursor (above or before)

### Visual Mode

- **`v`**: **V**isual mode for character-wise selection
- **`V`**: Visual mode for line-wise selection
- **`Ctrl + v`**: Visual block mode (useful for column selection)

### Indentation and Shifting

- **`>>`**: Shift line **right**
- **`<<`**: Shift line **left**

### Join

- **`J`**: Join Line bellow to current line (works with counts `3J` for example)
### Undo and Redo

- **`u`**: **U**ndo
- **`Ctrl + r`**: **R**edo

### Searches

- **`/`**: Search forward
- **`?`**: Search backward
- **`n`**: Repeat the search in the same direction (think **n**ext)
- **`N`**: Repeat the search in the opposite direction

### Text Object Selection (In Visual Mode)

- **`ciw`**: **C**hange **i**nside **w**ord
- **`diw`**: **D**elete **i**nside **w**ord
- **`caw`**: **C**hange **a**round **w**ord (includes surrounding spaces)
- **`cit`**: **C**hange **i**nside **t**ag (works well with HTML/XML tags)
- **`das`**: **D**elete **a**round **s**entence (includes spaces around it)

### Text Object Motions with Surroundings

- **`iw`**: **I**nside **w**ord (just the word, no spaces)
- **`aw`**: **A**round **w**ord (includes surrounding spaces)
- **`ip`**: **I**nside **p**aragraph
- **`ap`**: **A**round **p**aragraph (includes newline if at end of paragraph)
- **`it`**: **I**nside **t**ag (text inside HTML/XML tag)

### Jumps and Marks

- **`m` + letter**: Set a **m**ark (e.g., `ma` sets mark "a")
    - Capital letter sets global marks
- **`` ` `` + letter**: Jump to a specific mark (e.g., `` `a `` jumps to mark "a")
- **`` ' `` + letter**: Jump to line of specific mark (e.g., `` 'a `` jumps to mark "a")
- **`` ` ``**: Go back to the last cursor position (great for quickly undoing movements)
- **`` ' ``**: Go back to the last line (great for quickly undoing movements)

### Folding (Code/Document Structure)

- **`za`**: **Z**ap **a** fold (toggle open/close the current fold)
- **`zc`**: **Z**ip **c**lose the current fold
- **`zo`**: **Z**ip **o**pen the current fold
- **`zR`**: **Z**ip open **R**eveal all folds in the document
- **`zM`**: **Z**ip close all folds

### Registers (Clipboard-Like Features)

- **`"a` + command**: Use register **a** (for example, `"ayy` to yank a line into register "a")
- **`"+y`**: Yank to the system clipboard (think: `"+"` for global system clipboard)
- **`"+p`**: Paste from the system clipboard

### Window Management

- **`Ctrl + w s`**: **S**plit window **s**ideways (horizontal split)
- **`Ctrl + w v`**: **V**ertical split window
- **`Ctrl + w w`**: **W**indow **w**arp (cycle between open windows)
- **`Ctrl + w c`**: **C**lose current window

### Substitute and Replace

- **`:%s/foo/bar/g`**: Substitute all instances of "foo" with "bar" in the file (think `s` for **s**ubstitute)
- **`:s/foo/bar/gc`**: Substitute with **c**onfirmation (**c**heck before changing each match)

### Working with Multiple Files

- **`:e filename`**: **E**dit a new file
- **`:bnext`** or **`:bn`**: Switch to the **n**ext buffer (file)
- **`:bprev`** or **`:bp`**: Switch to the **p**revious buffer
- **`:bd`**: **B**uffer **d**elete (close the current file)

### Code Navigation (Specific to Code Files)

- **`gd`**: **G**o to **d**efinition (local)
- **`gD`**: Go to **g**lobal **D**efinition
- **`%`**: Jump to matching bracket, parenthesis, or tag (helpful for code blocks)

### Changing Case

- **`~`**: Toggle case of the character under the cursor
- **`gU` + motion**: Change to **U**ppercase for the specified motion (e.g., `gUw` to capitalize a word)
- **`gu` + motion**: Change to **l**owercase for the specified motion (e.g., `guw` to make a word lowercase)

### Miscellaneous

- **`.`**: Repeat the last edit (like a redo for commands)
- **`Ctrl + a`**: Increment the number under the cursor (**A**dd to number)
- **`Ctrl + x`**: Decrement the number under the cursor (**X** marks the spot and reduces it)

### g
In Vim, `g` is a "prefix" for various motions and commands, adding versatility to navigation and editing. Here are some common uses:

1. **`g` with motion keys**:
    
    - **`gg`**: Move to the beginning of the file.
    - **`G`**: Move to the end of the file (without `g`, but worth mentioning since it's related).
    - **`gd`**: Go to the local declaration of the variable or function under the cursor.
    - **`gD`**: Go to the global declaration of the variable or function under the cursor.
    - **`gi`**: Move the cursor to the last place where you inserted text and enter Insert mode.
2. **`g` with line-oriented commands**:
    
    - **`gu` + motion**: Convert text to lowercase (e.g., `guw` converts one word to lowercase).
    - **`gU` + motion**: Convert text to uppercase (e.g., `gUw` converts one word to uppercase).
3. **`g` with search commands**:
    
    - **`gn`**: Search forward for the next instance of the last search term and visually select it.
    - **`gN`**: Search backward for the last search term and visually select it.
4. **`g` for cursor positioning**:
    
    - **`g;`**: Move to the previous position in the change list.
    - **`g,`**: Move to the next position in the change list.
5. **File and text-related commands**:
    
    - **`gf`**: Go to the file name under the cursor (opens the file if it exists).
    - **`gx`**: Open the URL under the cursor in the system's default web browser.

The `g` key essentially extends Vim's basic motions and commands with additional, often more specialized actions. Let me know if you'd like any of these explained in detail!

### Movement by Search and Matching

- **`f<char>`**: **F**ind the next occurrence of **char** on the current line (e.g., `ft` finds the next "t")
- **`F<char>`**: Find **backwards** to the previous occurrence of **char**
- **`t<char>`**: Find the next occurrence of **char** on the current line and put the cursor before it. **T**ill occurrence (e.g., `tt` finds the next "t")
- **`;`**: Repeat the last **f**ind command in the same direction (for `f`, `t`, etc.)
- **`,`**: Repeat the last **f**ind command in the **opposite** direction

### Jumping with Screen Movements

- **`H`**: Move to the **H**igh (top) of the screen
- **`M`**: Move to the **M**iddle of the screen
- **`L`**: Move to the **L**ow (bottom) of the screen

### Scrolling Within the Window

- **`Ctrl + y`**: Scroll **y**onder up (one line up)
- **`Ctrl + b`**: **B**ack one full page (up)
- **`Ctrl + u`**: **U**p half a page
- **`Ctrl + d`**: **D**own half a page
- **`Ctrl + f`**: **F**orward one full page (down)
- **`Ctrl + e`**: Scroll **e**ven lower (one line down)

### Advanced Search and Replace

- **`*`**: Search for the word under the cursor **forwards** (like a "starred" word)
- **`#`**: Search for the word under the cursor **backwards** (like "numbering" backwards)
- **`:%s/old/new/g`**: **S**ubstitute **old** with **new** throughout the file

### Undo and Redo History Movements

- **`g;`**: Move **b**ack through the **c**hange list (prior edits)
- **`g,`**: Move **f**orward through the **c**hange list

### Incremental/Decremental Changes with `g`

- **`g+`**: Move **forward** by **time** (e.g., go to the next edit in history)
- **`g-`**: Move **back** in **time** (e.g., go to the previous edit in history)

### Command-Line Mode and Useful Commands

- **`:`**: Enter command-line mode (think **:** for commands)
- **`:q`**: **Q**uit the current file
- **`:w`**: **W**rite (save) the current file
- **`:x`**: **X**it (save and quit combined, shorthand for `:wq`)
- **`:q!`**: Quit without saving changes (adding `!` is a way to "override")

### Registers for Copying/Pasting

- **`"_d`**: **_D**iscard — deletes without copying to a register (useful for deleting without affecting the clipboard)
- **`"*p`**: Paste from the system clipboard (think `*` as **s**ystem clipboard)

### Navigation with `g`

- **`g0`**: Go to the **b**eginning of the current screen line
- **`g$`**: Go to the **e**nd of the current screen line

### Exiting and Saving Commands

- **`:wa`**: **W**rite **a**ll open files (saves all changes)
- **`:qa`**: **Q**uit **a**ll open files
- **`:xa`**: e**X**it **a**ll (saves all and closes)

### Working with Indentation

- **`=G`**: Reindent from the cursor to the **G**round (end) of the file
- **`=gg`**: Reindent from the cursor to the **g**round (start) of the file

### **Using a Vim Plugin (Like `vim-commentary` or `NERD Commenter`)**

Vim plugins like `vim-commentary` or `NERD Commenter` simplify commenting:

- **vim-commentary**:
    - Select lines in Visual mode and press `gc` to toggle comments.
    - Or, use `gcc` to comment out the current line in Normal mode.