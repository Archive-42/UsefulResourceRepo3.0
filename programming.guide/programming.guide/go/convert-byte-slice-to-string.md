



## Further Reading

[String handling cheat sheet](string-functions-reference-cheat-sheet.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Strings, bytes, runes and characters in Go](https://blog.golang.org/strings)  
<span style="color: grey; font-style: italic; font-size: smaller">The Go Blog</span>

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

# Go: Convert byte slice (array) to string

Converting a slice of bytes to a string yields a string whose bytes are the elements of the slice:

    b := []byte{'a', 'b', 'c', '\xe6', '\x97', '\xa5'}
    s := string(b)
    fmt.Println(s)
    // Output: abc日

## Arrays

If `b` is an array, slice it first using `b[:]`:

    s := string(b[:])

## Comments (2)

![User avatar](https://www.gravatar.com/avatar/018d61a7452fce6ca7801c083f8d9517?d=mp)

I run into this error: `cannot convert hashed (type [32]byte) to type string.`

<span style="color: grey">by nitohu | </span> <span class="reply-button">Reply</span>

![User avatar](https://www.gravatar.com/avatar/99e100243aaa8b1469b1ed4e8bbecb06?d=mp)

A `[32]byte` is an array. Convert it to a slice first: `string(hashes[:])`.

<span style="color: grey">by Andreas Lundblad | </span> <span class="reply-button">Reply</span>

### Add comment

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
