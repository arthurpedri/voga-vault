`|` - Pipe will send the stdout of the command into the stdin of the next: `cmdthatoutputs | cmdthatreceivestheinput`
`$$` - Will run the next command after the one before finished successfully.
`;` - Will run the next command regardless of the success of the previous one.

## Echo
```bash
echo $variable
```
## Variable
```bash
variablename="value"
```

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