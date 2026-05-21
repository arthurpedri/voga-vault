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