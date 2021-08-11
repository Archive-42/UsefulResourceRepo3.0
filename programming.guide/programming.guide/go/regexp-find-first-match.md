<span class="underline"></span>

<span class="underline"></span>

Further reading
---------------

[Regular expressions](regexp-cheat-sheet.html)  
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

Go: Find first substring matching a regexp
==========================================

Use the [`FindString`](https://golang.org/pkg/regexp/#Regexp.FindString) method to find the **text of the first match**. If there is no match, the return value is an empty string.

    re := regexp.MustCompile(`foo.?`)
    fmt.Printf("%q\n", re.FindString("seafood fool")) // "food"
    fmt.Printf("%q\n", re.FindString("meat"))         // ""

There are several more search functions available in the [`regexp`](https://golang.org/pkg/regexp/) package. The strings `All`, `String`, `Submatch`, and `Index` can be combined to form the methods:

    Find(All)?(String)?(Submatch)?(Index)?

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
