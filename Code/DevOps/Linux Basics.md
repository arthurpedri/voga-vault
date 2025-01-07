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