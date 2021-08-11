



## Further Reading

[Slices explained](slices-explained.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Empty slice vs. nil slice](nil-slice-vs-empty-slice.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

## Top Go Articles

1.  [Go gotcha](go-gotcha.html)
2.  [String handling cheat sheet](string-functions-reference-cheat-sheet.html)
3.  [Maps explained](maps-explained.html)
4.  [For loops explained](for-loop.html)
5.  [Concurrent programming](go-concurrency-tutorial.html)

[**See all 197 Go articles**](index.html)



## Top Algorithm Articles

1.  [Dynamic programming vs memoization vs tabulation](../dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](../big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](../sliding-window-example.html)
4.  [What makes a good loop invariant?](../what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](../random-point-within-circle.html)

[**See all articles**](../index.html)

# Go: Clear a slice

To remove all elements, set the slice to `nil`:

    a := []string{"A", "B", "C", "D", "E"}
    a = nil
    fmt.Println(a, len(a), cap(a)) // [] 0 0

This will release the underlying array to the garbage collector (assuming there are no other references).

Note that nil slices and empty slices are very similar:

- they look the same when printed,
- they have zero length and capacity,
- they can be used with the same effect in for loops and append functions.

## Keep allocated memory

To keep the underlying array, slice the slice to zero length:

    a := []string{"A", "B", "C", "D", "E"}
    a = a[:0]
    fmt.Println(a, len(a), cap(a)) // [] 0 5

If the slice is extended again, the original data reappears:

    fmt.Println(a[:2]) // [A B]

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
