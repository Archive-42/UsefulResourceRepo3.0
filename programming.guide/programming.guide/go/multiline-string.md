<span class="underline"></span>

<span class="underline"></span>

## Further Reading

[String handling cheat sheet](string-functions-reference-cheat-sheet.html)  
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

# Go: Multiline strings

## Raw string literals

Raw string literals, delimited by **back quotes**, can contain line breaks.

    str := `First line.
    Second line.`
    fmt.Println(str)

    First line.
    Second line.

Raw strings literals are interpreted literally and backslashes have no special meaning.

## Interpreted string literals

To insert escape characters, use interpreted string literals delimited by **double quotes**.

    str := "\tFirst line.\n" +
    "Second line."
    fmt.Println(str)

          First line.
    Second line.

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
