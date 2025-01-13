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
## File types
File types are the first character in `ls -l`
- `-` means a normal file, could be a executable file too
- `d` directory
- `b` block device (or block special file), like `sda`, `sda1`, etc..
- `c` character special file (or character device), pipes, serial ports. Writing and reading is an immediate action. Writing a byte could cause it to be displayed on screen, output on a serial port, converted into a sound, etc..
- `l` link
- `s` socket
- `p` pipes



[[Linux Commands]]
[[Linux Filters]]
[[Linux IO Redirection]]