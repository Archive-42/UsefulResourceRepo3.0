## Further reading

[Regular expressions](regexp-cheat-sheet.html)  
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

# Go: Find the location of a regexp substring match

Use the [`FindStringIndex`](https://golang.org/pkg/regexp/#Regexp.FindStringIndex) method to find `loc`, the **location of the first match**, in a string `s`. The match is at `s[loc[0]:loc[1]]`. A return value of nil indicates no match.

    re := regexp.MustCompile(`ab?`)
    fmt.Println(re.FindStringIndex("tablett"))    // [1 3]
    fmt.Println(re.FindStringIndex("foo") == nil) // true

There are several more search functions available in the [`regexp`](https://golang.org/pkg/regexp/) package. The strings `All`, `String`, `Submatch`, and `Index` can be combined to form the methods:

    Find(All)?(String)?(Submatch)?(Index)?

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
