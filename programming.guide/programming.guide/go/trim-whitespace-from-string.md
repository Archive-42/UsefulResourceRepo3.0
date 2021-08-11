<span class="underline"></span>

<span class="underline"></span>

## Related

[Remove duplicate whitespace from a string](remove-duplicate-whitespace.html)  
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

# Go: How to trim leading and trailing whitespace from a string

Use the [`strings.TrimSpace`](https://golang.org/pkg/strings/#TrimSpace) function to remove leading and trailing whitespace (as defined by Unicode):

    s := strings.TrimSpace("\t Hello world!\n ")
    fmt.Printf("%q", s)
    // Output: "Hello world!"

To remove other leading and trailing characters, use [`strings.Trim`](https://golang.org/pkg/strings/#Trim). To remove only the leading or the trailing characters, use [`strings.TrimLeft`](https://golang.org/pkg/strings/#TrimLeft) or [`strings.TrimRight`](https://golang.org/pkg/strings/#TrimRight).

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
