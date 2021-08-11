## Further Reading

[Untyped numeric constants with no limits](untyped-constants.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Constants](https://blog.golang.org/constants)  
<span style="color: grey; font-style: italic; font-size: smaller">The Go Blog</span>

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
17. [Numbers that start with zero](gotcha-octal-decimal-hexadecimal-literal.html)
18. [What's wrong with the remainder (modulo) operator?](gotcha-remainder-modulo-operator.html)
19. Why can't I multiply a time.Duration with an integer?
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

# Go gotcha: Why can't I multiply a time.Duration with an integer?

Why doesn't this compile?

    n := 100
    time.Sleep(n * time.Millisecond)

    invalid operation: n * time.Millisecond (mismatched types int and time.Duration)

Answer

There is no mixing of numeric types in Go. You can only multiply a `time.Duration` with

- another `time.Duration`, or
- an **untyped integer** constant.

Here are three correct examples:

    var n time.Duration = 100
    time.Sleep(n * time.Millisecond)

    const n = 100
    time.Sleep(n * time.Millisecond)

    time.Sleep(100 * time.Millisecond)

<a href="gotcha-remainder-modulo-operator.html" class="prev"></a>

« Prev

What's wrong with the remainder (modulo) operator?

[](go-gotcha.html#toc)

TOC

Go gotcha

19 of 26

<a href="gotcha-index-out-of-range.html" class="next"></a>

Next »

Why is this index out of range?

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
