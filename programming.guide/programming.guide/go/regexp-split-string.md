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

Go: Split a string using regexp delimiter
=========================================

Use the [`Split`](https://golang.org/pkg/regexp/#Regexp.Split) method to **slice a string into substrings** separated by the regexp. It returns a slice of the substrings between those expression matches. A return value of nil indicates no match.

The method takes an integer argument `n`; if `n >= 0`, the function returns at most `n` matches.

    a := regexp.MustCompile(`a`)
    fmt.Printf("%q\n", a.Split("banana", -1)) // ["b" "n" "n" ""]
    fmt.Printf("%q\n", a.Split("banana", 0))  // [] (nil slice)
    fmt.Printf("%q\n", a.Split("banana", 1))  // ["banana"]
    fmt.Printf("%q\n", a.Split("banana", 2))  // ["b" "nana"]

    zp := regexp.MustCompile(`z+`)
    fmt.Printf("%q\n", zp.Split("pizza", -1)) // ["pi" "a"]
    fmt.Printf("%q\n", zp.Split("pizza", 0))  // [] (nil slice)
    fmt.Printf("%q\n", zp.Split("pizza", 1))  // ["pizza"]
    fmt.Printf("%q\n", zp.Split("pizza", 2))  // ["pi" "a"]

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
