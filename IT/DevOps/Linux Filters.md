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
