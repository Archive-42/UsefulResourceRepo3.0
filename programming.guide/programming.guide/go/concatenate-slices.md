<span class="underline"></span>

<span class="underline"></span>

## Further Reading

[Append function explained](append-explained.html)  
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

# Go: Concatenate slices

Use [`append`](append-explained.html) and add dots after the second slice:

    a := []int{1, 2}
    b := []int{11, 22}
    a = append(a, b...) // a == [1 2 11 22]

The `...` unpacks `b`. Without the dots, the code would attempt to append the slice as a whole, which is invalid since `a` is not a slice of slices.

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
