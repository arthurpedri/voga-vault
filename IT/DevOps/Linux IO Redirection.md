## Black hole `/dev/null`
- Anything written here will disappear an cannot be recovered
- Reading from here will return nothing
## File Output `>` or `1>`
- Replace contents in destination
## File Output `>>` or `1>>`
- Append contents in destination
## Error output `2>` or `2>>`
- Outputs `stderr` to destination
## Any output `&>` and `&>>`
- Sends all outputs to destination
## Piping `|`
- Sends `stdout` of one command to `stdin` of another
```bash
ls | wc
# is equivalent to
ls > tempfile
wc < tempfile
```
