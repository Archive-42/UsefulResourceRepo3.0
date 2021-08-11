<span class="underline"></span>

<span class="underline"></span>

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

<span class="underline"></span>

## Top Algorithm Articles

1.  [Dynamic programming vs memoization vs tabulation](../dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](../big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](../sliding-window-example.html)
4.  [What makes a good loop invariant?](../what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](../random-point-within-circle.html)

[**See all articles**](../index.html)

# Go: Convert string to rune slice (array)

Converting a string to a slice of runes yields a slice whose elements are the Unicode code points of the string.

    s := "abc日"
    r := []rune(s)
    fmt.Printf("%v\n", r)
    fmt.Printf("%U\n", r)
    // Output:
    // [97 98 99 26085]
    // [U+0061 U+0062 U+0063 U+65E5]

## Comments (1)

![User avatar](https://www.gravatar.com/avatar/f95508db25875bb30c3aeab289863043?d=mp)

Really helpful, thanks!

<span style="color: grey">by roxy | </span> <span class="reply-button">Reply</span>

### Add comment

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
