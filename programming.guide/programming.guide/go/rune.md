<span class="underline"></span>

<span class="underline"></span>

Further Reading
---------------

[String handling cheat sheet](string-functions-reference-cheat-sheet.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Unicode character table](https://unicode-table.com/en/)  
<span style="color: grey; font-style: italic; font-size: smaller">unicode-table.com</span>

[Strings, bytes, runes and characters in Go](https://blog.golang.org/strings)  
<span style="color: grey; font-style: italic; font-size: smaller">The Go Blog</span>

[UTF-8: Bits, Bytes, and Benefits](https://research.swtch.com/utf8)  
<span style="color: grey; font-style: italic; font-size: smaller">by Russ Cox</span>

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

Go: What is a rune?
===================

Unicode code points
-------------------

A rune is a type meant to represent a Unicode code point.

The `rune` type is an alias for `int32`, and is used to emphasize than an integer represents a code point.

**ASCII** defines 128 characters, identified by the **code points** 0–127. It covers English letters, Latin numbers, and a few other characters.

**Unicode**, which is a superset of ASCII, defines a codespace of 1,114,112 code points. Unicode version 10.0 covers 139 modern and historic scripts, as well as multiple symbol sets.

Strings and UTF-8
-----------------

A Go string is an immutable sequence of bytes. It *typically* contains text encoded as UTF-8.

Note that a `string` is a sequence of bytes, not runes.

However, strings often contain Unicode text encoded in [*UTF-8*](https://research.swtch.com/utf8), which encodes all Unicode code points using one to four bytes, and Go source code is always encoded in UTF-8. This encoding was in fact designed by Ken Thompson and Rob Pike, two of the main creators of Go.

The [*String handling cheat sheet*](string-functions-reference-cheat-sheet.html) covers the principal ways to handle strings and runes in Go.

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
