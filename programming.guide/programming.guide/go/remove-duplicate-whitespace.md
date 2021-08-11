<span class="underline"></span>

<span class="underline"></span>

Related
-------

[Regular expressions](regexp-cheat-sheet.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[How to trim leading and trailing whitespace from a string](trim-whitespace-from-string.html)  
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

Go: Remove duplicate whitespace from a string
=============================================

    space := regexp.MustCompile(`\s+`)
    str := space.ReplaceAllString("Hello  \t \n world!", " ")
    fmt.Println(str) // "Hello world!"

`\s+` is a [regular expression](regexp-cheat-sheet.html). The character class `\s` matches a space, tab, new line, carriage return or form feed, and `+` says “one or more of those”. In other words, the code will replace all whitespace substrings with a single space character.

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
