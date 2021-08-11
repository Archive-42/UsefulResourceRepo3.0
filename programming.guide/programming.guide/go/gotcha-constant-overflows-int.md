## Further Reading

[Conversions](conversions.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Untyped numeric constants with no limits](untyped-constants.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Variadic functions (...T)](variadic-function.html)  
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
12. Why can't I print large numbers? (constant overflows int)
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

# Go gotcha: Why can't I print large numbers? (constant overflows int)

Why doesn't this code compile?

    const n = 9876543210 * 9876543210
    fmt.Println(n)

    ../main.go:2:13: constant 97546105778997104100 overflows int

Answer

The untyped constant `n` must be converted to a type before it can be assigned to the `interface{}` parameter in the call to

    fmt.Println(a ...interface{})

When the type can’t be inferred from the context, an untyped constant is converted to a `bool`, `int`, `float64`, `complex128`, `string` or `rune` depending of the format of the constant.

In this case the constant is an integer, but `n` is larger than the maximum value of an `int`.

However, `n` can be represented as a `float64`:

    const n = 9876543210 * 9876543210
    fmt.Println(float64(n))

    9.75461057789971e+19

For exact representation of big numbers, the [math/big](https://golang.org/pkg/math/big/) package implements arbitrary-precision arithmetic. It supports signed integers, rational numbers and floating-point numbers.

<a href="gotcha-append.html" class="prev"></a>

« Prev

Why doesn't append work every time?

[](go-gotcha.html#toc)

TOC

Go gotcha

12 of 26

<a href="gotcha-increment-decrement-statement.html" class="next"></a>

Next »

Why doesn't increment (++) and decrement (--) work?

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
