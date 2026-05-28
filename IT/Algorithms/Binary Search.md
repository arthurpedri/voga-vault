### Pseudocode
Given two inputs:
1. A list of `n` elements **sorted** from least to greatest
2. A `target` value:
Do the following:
- Set low = 0 and high = `n - 1`.
- While low <= high:
    - Set median (the position of the middle element) to `(low + high) // 2`, which is the greatest integer less than or equal to `(low + high) / 2`
    - If `list[median]` == `target`, return `True` or `median index`
    - Else if `list[median]` < `target`, set low to `median + 1`
    - Otherwise set high to `median - 1`
- Return `False` or `-1`