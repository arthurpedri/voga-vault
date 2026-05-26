# Commands
- Range in command `touch file{1..10}.txt` creates 10 files from `file1.txt` to `file10.txt`
- `ln -s` soft link
- `ls`
    - `-t` sort by time
    - `-r` reverse sort order
    - `-l` long
    - `-h` human readable
- `file` check file type
- `df` overview of filesystem disk space usage
- `wc` counts lines, words and bytes
- `find` finds file or directory
- `locate` fast find, using a database that is updated on a schedule. To use as a real time search the database has to be updated first to ensure correctness
- `history` command history
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

## Kill
```bash
kill <PID>
ps aux # process status list all, including owned by other users and show extra information
```
