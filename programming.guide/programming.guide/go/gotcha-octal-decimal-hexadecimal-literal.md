## Further Reading

[Bitwise operators cheat sheet](bitwise-operator-cheat-sheet.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

## Go gotcha

1.  [Why can't I add elements to my map?](gotcha-assignment-entry-nil-map.html)
2.  [What's a nil pointer dereference?](gotcha-nil-pointer-dereference.html)
3.  [Multiple values in single value context?](gotcha-multiple-value-sinlge-value-context.html)
4.  [Why doesn't this function change my array?](gotcha-function-doesnt-change-array.html)
5.  [Two variables with the same name?](gotcha-shadowing-variables.html)
6.  [Extra comma in slice literal](gotcha-missing-comma-slice-array-map-literal.html)
7.  [Why can't I update my string?](gotcha-strings-are-immutable.html)
8.  [Why aren't the characters concatenated?](gotcha-concatenate-rune-string.html)
9.  [What happened to ABBA?](gotcha-trim-string.html)
10. [What happened to my copy?](gotcha-copy-missing.html)
11. [Why doesn't append work every time?](gotcha-append.html)
12. [Why can't I print large numbers? (constant overflows int)](gotcha-constant-overflows-int.html)
13. [Why doesn't increment (++) and decrement (--) work?](gotcha-increment-decrement-statement.html)
14. [Why is my computation wrong?](gotcha-operator-precedence.html)
15. [Why does Go and Pythagoras disagree?](gotcha-bitwise-operators.html)
16. [Why doesn't this loop end?](gotcha-integer-overflow-wrap-around.html)
17. Numbers that start with zero
18. [What's wrong with the remainder (modulo) operator?](gotcha-remainder-modulo-operator.html)
19. [Why can't I multiply a time.Duration with an integer?](gotcha-multiply-duration-integer.html)
20. [Why is this index out of range?](gotcha-index-out-of-range.html)
21. [Unexpected values in range loop](gotcha-unexpected-values-range.html)
22. [Can't change entries in range loop](gotcha-change-value-range.html)
23. [Iteration variable doesn't see change in range loop](gotcha-range-copy-array.html)
24. [Iteration variables and closures](gotcha-data-race-closure.html)
25. [Why is the JSON output empty?](gotcha-json-marshal-empty.html)
26. [Why is nil not equal to nil?](gotcha-why-nil-error-not-equal-nil.html)

## Top Go Articles

1.  [Go gotcha](go-gotcha.html)
2.  [Go: String handling cheat sheet](string-functions-reference-cheat-sheet.html)
3.  [Go: Maps explained](maps-explained.html)
4.  [Go: For loops explained](for-loop.html)
5.  [Go: Concurrent programming](go-concurrency-tutorial.html)

[**See all 197 Go articles**](index.html)

## Top Algorithm Articles

1.  [Dynamic programming vs memoization vs tabulation](../dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](../big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](../sliding-window-example.html)
4.  [What makes a good loop invariant?](../what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](../random-point-within-circle.html)

[**See all articles**](../index.html)

# Go gotcha: Numbers that start with zero

What's going on with the counting in this example?

    const (
            Century = 100
            Decade  = 010
            Year    = 001
    )
    // The world's oldest person, Emma Morano, lived for a century,
    // two decades and two years.
    fmt.Println("She was", Century+2*Decade+2*Year, "years old.")

    She was 118 years old.

Answer

`010` is a number in **base 8**, therefore it means 8, not 10.

Integer literals in Go are specified in octal, decimal or hexadecimal. The number 16 can be written as `020`, `16` or `0x10`.

<table><thead><tr class="header"><th>Literal</th><th>Base</th><th>Note</th></tr></thead><tbody><tr class="odd"><td><code>020</code></td><td>8</td><td>Starts with <code>0</code></td></tr><tr class="even"><td><code>16</code></td><td>10</td><td>Never starts with <code>0</code>*</td></tr><tr class="odd"><td><code>0x10</code></td><td>16</td><td>Starts with <code>0x</code></td></tr></tbody></table>

\* `0` is an octal literal in Go.

An integer literal is a sequence of digits representing an integer constant. An optional prefix sets a non-decimal base: 0 for octal, 0x or 0X for hexadecimal. <a href="https://golang.org/ref/spec#Integer_literals" class="quote-source">The Go Programming Language Specification: Integer literals</a>

<a href="gotcha-integer-overflow-wrap-around.html" class="prev"></a>

« Prev

Why doesn't this loop end?

[](go-gotcha.html#toc)

TOC

Go gotcha

17 of 26

<a href="gotcha-remainder-modulo-operator.html" class="next"></a>

Next »

What's wrong with the remainder (modulo) operator?

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
