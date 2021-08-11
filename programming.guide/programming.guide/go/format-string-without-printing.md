<span class="underline"></span>

<span class="underline"></span>

Further Reading
---------------

[Print with fmt cheat sheet](fmt-printf-reference-cheat-sheet.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

Top Go Articles
---------------

1.  [Go gotcha](go-gotcha.html)
2.  [String handling cheat sheet](string-functions-reference-cheat-sheet.html)
3.  [Maps explained](maps-explained.html)
4.  [For loops explained](for-loop.html)
5.  [Concurrent programming](go-concurrency-tutorial.html)

[**See all 197 Go articles**](index.html)

<span class="underline"></span>

Top Algorithm Articles
----------------------

1.  [Dynamic programming vs memoization vs tabulation](../dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](../big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](../sliding-window-example.html)
4.  [What makes a good loop invariant?](../what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](../random-point-within-circle.html)

[**See all articles**](../index.html)

Go: Format a string without printing it
=======================================

The [`fmt.Sprintf`](https://golang.org/pkg/fmt/#Sprintf) function formats a string in the same way as [`fmt.Printf`](https://golang.org/pkg/fmt/#Printf), but returns the string instead of printing it.

    s := fmt.Sprintf("Size: %d MB.", 85)
    fmt.Println(s)
    // Output: Size: 85 MB.

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)