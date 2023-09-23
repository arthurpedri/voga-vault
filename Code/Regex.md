- `^`: asserts position at start of a line.
- `.`: any character (except line terminators).
- `+`: matches previous token between one and unlimited times, as many as possible.
- `$`: asserts position at the end of a line.


#### Removing HTML Tags
- `<[^>]*>`
#### Selecting headers HTML
- `<h.*?<\/h.>`

^(.+)$
"$1",

