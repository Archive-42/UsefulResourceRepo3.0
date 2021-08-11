<span class="underline"></span>

<span class="underline"></span>

## Further Reading

[Slices explained](slices-explained.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Time complexity explained](../time-complexity-explained.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Clear a slice](clear-slice.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Copy function explained](copy-explained.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Default value of struct, string, slice, map](default-zero-value.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

## Top Go Articles

1.  [Go gotcha](go-gotcha.html)
2.  [String handling cheat sheet](string-functions-reference-cheat-sheet.html)
3.  [Maps explained](maps-explained.html)
4.  [For loops explained](for-loop.html)
5.  [Concurrent programming](go-concurrency-tutorial.html)

[**See all 197 Go articles**](index.html)

<span class="underline"></span>

## Top Algorithm Articles

1.  [Dynamic programming vs memoization vs tabulation](../dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](../big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](../sliding-window-example.html)
4.  [What makes a good loop invariant?](../what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](../random-point-within-circle.html)

[**See all articles**](../index.html)

# Go: Delete an element from a slice

Here's how to remove the element at index `i` from a slice.

## Fast version (changes order of elements):

    a := []string{"A", "B", "C", "D", "E"}
    i := 2

    a[i] = a[len(a)-1] // Copy last element to index i
    a[len(a)-1] = ""   // Erase last element (write zero value)
    a = a[:len(a)-1]   // Truncate slice

    fmt.Println(a) // [A B E D]

This is fast: the code copies a single element and runs in **constant time**.

## Slow version (maintains order of elements):

    a := []string{"A", "B", "C", "D", "E"}
    i := 2

    copy(a[i:], a[i+1:]) // Shift a[i+1:] left one index
    a[len(a)-1] = ""     // Erase last element (write zero value)
    a = a[:len(a)-1]     // Truncate slice

    fmt.Println(a) // [A B D E]

This could be slow: the code copies len(a) − i − 1 elements and runs in **linear time**.

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
