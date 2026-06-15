Selection sort pseudocode:

1.  For each index:
    1.  Set `smallest_idx` to the current index (of the outer loop)
    2.  For each index from `i + 1` to the end of the list:
        1.  If the number at the inner loop index is smaller than the number at `smallest_idx`, set `smallest_idx` to the inner loop index
    3.  Swap the number at the outer loop index with the number at `smallest_idx`
2.  Return the sorted list