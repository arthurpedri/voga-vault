- Everything is a file
- Small single purpose programs
- Ability to chain programs together for complex operations
- Avoid Captive User Interface
    - Needing user input to continue, etc..
- Configuration stored in text files
## Important directories
- Home directories: `/root, /home/username`
- User Executable: `/bin, /usr/bin, /usr/local/bin`
- System Executables: `/sbin, /usr/sbin, /usr/local/sbin`
    - Only executable by root
- Other Mountpoints: `/media, /mnt`
    - External devices, usb, cd
- Configuration: `/etc`
- Temporary Files: `/tmp`
    - Useful for automation helpers
- Kernels and Bootloader: `/boot`
- Server Data: `/var, /srv`
- System Information: `/proc, /sys`
- Shared Libraries: `/lib, /usr/lib, /usr/local/lib`

# Commands
- Range in command `touch file{1..10}.txt` creates 10 files from `file1.txt` to `file10.txt`
- `ln -s` soft link
- `ls`
    - `-t` sort by time
    - `-r` reverse sort order
    - `-l` long
    - `-h` human readable
- `file` check file type
# File Types
File types are the first character in `ls -l`
- `-` means a normal file, could be a executable file too
- `d` directory
- `b` block device (or block special file), like `sda`, `sda1`, etc..
- `c` character special file (or character device), pipes, serial ports. Writing and reading is an immediate action. Writing a byte could cause it to be displayed on screen, output on a serial port, converted into a sound, etc..
- `l` link
- `s` socket
- `p` pipes
# Filters
## Grep
Search for text
- `-i` ignore case
- `-r/-R` recursive / dereference recursive
- `-v` invert match
## More/less/head/tail
- `tail -f` (follow) keeps file open and shows changes made, useful for logs
## Cut
- `cut --delimiter "," --fields 1` (`cut -d, -f1`)
## Awk
- `awk '{s+=$1} END {print s}' path/to/file`
## Sed
- `sed 's/apple/mango/g'`
    - `-i` edit in place