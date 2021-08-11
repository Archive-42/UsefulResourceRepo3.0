<span class="underline"></span>

<span class="underline"></span>

Further Reading
---------------

[String handling cheat sheet](string-functions-reference-cheat-sheet.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[How to split a string into a slice](split-string-into-slice.html)  
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

Go: How to split a string into a slice
======================================

Split
-----

Use the [`strings.Split`](https://golang.org/pkg/strings/#Split) function to split a string into its comma separated values:

    s := strings.Split("a,b,c", ",")
    fmt.Println(s)
    // Output: [a b c]

To include the separators, use [`strings.SplitAfter`](https://golang.org/pkg/strings/#SplitAfter). To split only the first n values, use [`strings.SplitN`](https://golang.org/pkg/strings/#SplitN) and [`strings.SplitAfterN`](https://golang.org/pkg/strings/#SplitAfterN).

Fields
------

Use the [`strings.Fields`](https://golang.org/pkg/strings/#Fields) function to split a string into substrings removing white space:

    s := strings.Fields(" a \t b \n")
    fmt.Println(s)
    // Output: [a b]

For more complex cases, use regular expressions.

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
