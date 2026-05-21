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
## Touch
- Touch updates access and modification timestamps of a file
    - Creating a file that does not exist is a side-effect, so it is useful when scripting to ensure a file exists

## Symbolic Links
### Link
```bash
ln -s target_path link_path
```
- `-s` creates a symbolic link

## Grep
```bash
grep "hello" words.txt
grep -r "hello" .
```

## Find
```bash
find directory -name "*arthur*.txt"
```

## Permissions
### Chmod
```bash
chmod -R u=rwx,g=,o= directory
chmod u+x file
chmod -x file
chmod g-rw file
```
### Chown
```bash
sudo chown -R root directory
```

## Shebang
```bash
#! interpreter [optional-arg]
#!/usr/bin/python3
```

## Environment Variable
```bash
env
export NAME="Arthur"
echo $NAME
```

### Path
```bash
export PATH="$PATH:/path/to/new/location"
```


[[Linux Commands]]
[[Linux Filters]]
[[Linux IO Redirection]]