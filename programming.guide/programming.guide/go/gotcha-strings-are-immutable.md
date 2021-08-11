<span class="underline"></span>

<span class="underline"></span>

Further Reading
---------------

[What is a rune?](rune.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[String handling cheat sheet](string-functions-reference-cheat-sheet.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Convert rune slice (array) to string](convert-rune-slice-to-string.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Convert string to rune slice (array)](convert-string-to-rune-slice.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

Go gotcha
---------

1.  [Why can't I add elements to my map?](gotcha-assignment-entry-nil-map.html)
2.  [What's a nil pointer dereference?](gotcha-nil-pointer-dereference.html)
3.  [Multiple values in single value context?](gotcha-multiple-value-sinlge-value-context.html)
4.  [Why doesn't this function change my array?](gotcha-function-doesnt-change-array.html)
5.  [Two variables with the same name?](gotcha-shadowing-variables.html)
6.  [Extra comma in slice literal](gotcha-missing-comma-slice-array-map-literal.html)
7.  Why can't I update my string?
8.  [Why aren't the characters concatenated?](gotcha-concatenate-rune-string.html)
9.  [What happened to ABBA?](gotcha-trim-string.html)
10. [What happened to my copy?](gotcha-copy-missing.html)
11. [Why doesn't append work every time?](gotcha-append.html)
12. [Why can't I print large numbers? (constant overflows int)](gotcha-constant-overflows-int.html)
13. [Why doesn't increment (++) and decrement (--) work?](gotcha-increment-decrement-statement.html)
14. [Why is my computation wrong?](gotcha-operator-precedence.html)
15. [Why does Go and Pythagoras disagree?](gotcha-bitwise-operators.html)
16. [Why doesn't this loop end?](gotcha-integer-overflow-wrap-around.html)
17. [Numbers that start with zero](gotcha-octal-decimal-hexadecimal-literal.html)
18. [What's wrong with the remainder (modulo) operator?](gotcha-remainder-modulo-operator.html)
19. [Why can't I multiply a time.Duration with an integer?](gotcha-multiply-duration-integer.html)
20. [Why is this index out of range?](gotcha-index-out-of-range.html)
21. [Unexpected values in range loop](gotcha-unexpected-values-range.html)
22. [Can't change entries in range loop](gotcha-change-value-range.html)
23. [Iteration variable doesn't see change in range loop](gotcha-range-copy-array.html)
24. [Iteration variables and closures](gotcha-data-race-closure.html)
25. [Why is the JSON output empty?](gotcha-json-marshal-empty.html)
26. [Why is nil not equal to nil?](gotcha-why-nil-error-not-equal-nil.html)

<span class="underline"></span>

Top Go Articles
---------------

1.  [Go gotcha](go-gotcha.html)
2.  [Go: String handling cheat sheet](string-functions-reference-cheat-sheet.html)
3.  [Go: Maps explained](maps-explained.html)
4.  [Go: For loops explained](for-loop.html)
5.  [Go: Concurrent programming](go-concurrency-tutorial.html)

[**See all 197 Go articles**](index.html)

Top Algorithm Articles
----------------------

1.  [Dynamic programming vs memoization vs tabulation](../dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](../big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](../sliding-window-example.html)
4.  [What makes a good loop invariant?](../what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](../random-point-within-circle.html)

[**See all articles**](../index.html)

Go gotcha: Why can't I update my string?
========================================

Why doesn't this code compile:

    s := "hello"
    s[0] = 'H'
    fmt.Println(s)

    ../main.go:3:7: cannot assign to s[0]

Answer

Go strings are immutable and behave like read-only byte slices (with a few extra properties).

To update the data, use a rune slice instead:

    buf := []rune("hello")
    buf[0] = 'H'
    s := string(buf)
    fmt.Println(s)  // prints "Hello"

If the string only contains ASCII characters, you could also use a byte slice.

See [String handling cheat sheet](string-functions-reference-cheat-sheet.html) for an overview of strings in Go.

<a href="gotcha-missing-comma-slice-array-map-literal.html" class="prev"></a>

« Prev

Extra comma in slice literal

[](go-gotcha.html#toc)

TOC

Go gotcha

7 of 26

<a href="gotcha-concatenate-rune-string.html" class="next"></a>

Next »

Why aren't the characters concatenated?

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
