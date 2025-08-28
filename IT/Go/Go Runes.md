### Runes
- 32-bit integer values that represent ==Unicode code points==
- Similar to a *character* in C or any other language
- Runes are bigger than characters from other languages, they were made to represent many different types of characters, not just those in the alphabet
- The way indexing and len() work on runes are in line with runes (or int32) and not on bytes, like how `string`s work
- When you convert from `string` to `[]rune`, each utf-8 char in that string becomes a `rune`.
- Similarly, in the reverse conversion, when converting from `[]rune` to `string`, each `rune` becomes a utf-8 char in the `string`.
#### Range with strings and runes
- In strings, the `range` keyword helps by breaking out individual Unicode code points by parsing the UTF-8
```go
for pos, char := range "日本語" {
    fmt.Printf("character %c starts at byte position %d\n", char, pos)
}
// Prints
character 日 starts at byte position 0
character 本 starts at byte position 3
character 語 starts at byte position 6
// Getting first rune in a string:
s := "Hello, 世界" 
firstRune := []rune(s)[0] // Convert string to rune slice and get the first rune
```