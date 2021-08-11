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

Go: Find all substrings matching a regexp
=========================================

Use the [`FindAllString`](https://golang.org/pkg/regexp/#Regexp.FindAllString) method to find the **text of all matches**. A return value of nil indicates no match.

The method takes an integer argument `n`; if `n >= 0`, the function returns at most `n` matches.

    re := regexp.MustCompile(`a.`)
    fmt.Printf("%q\n", re.FindAllString("paranormal", -1)) // ["ar" "an" "al"]
    fmt.Printf("%q\n", re.FindAllString("paranormal", 2))  // ["ar" "an"]
    fmt.Printf("%q\n", re.FindAllString("graal", -1))      // ["aa"]
    fmt.Printf("%q\n", re.FindAllString("none", -1))       // [] (nil slice)

There are several more search functions available in the [`regexp`](https://golang.org/pkg/regexp/) package. The strings `All`, `String`, `Submatch`, and `Index` can be combined to form the methods:

    Find(All)?(String)?(Submatch)?(Index)?

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
