## Further Reading

[For loops explained](for-loop.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[What’s the maximum value of an int?](max-min-int-uint.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Numeric types](https://golang.org/ref/spec#Numeric_types)  
<span style="color: grey; font-style: italic; font-size: smaller">The Go Programming Language Specification</span>

[Print with fmt cheat sheet](fmt-printf-reference-cheat-sheet.html)  
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
16. Why doesn't this loop end?
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

# Go gotcha: Why doesn't this loop end?

Why does this loop run forever?

    var b byte
    for b = 250; b <= 255; b++ {
            fmt.Printf("%d %c\n", b, b)
    }

Answer

After the `b == 255` iteration, `b++` is executed. This overflows (since the maximum value for a byte is 255) and results in `b == 0`. Therefore `b <= 255` still holds and the loop restarts from 0.

For unsigned integer values, the operations +, -, \*, and &lt;&lt; are computed modulo 2<sup>n</sup>, where n is the bit width of the unsigned integer's type.

For signed integers, the operations +, -, \*, and &lt;&lt; may legally overflow and the resulting value exists and is deterministically defined by the signed integer representation, the operation, and its operands. No exception is raised as a result of overflow. <a href="https://golang.org/ref/spec#Arithmetic_operators" class="quote-source">The Go Programming Language Specification: Arithmetic operators</a>

If we use the standard loop idiom with a strict inequality, the compiler will catch the bug:

    var b byte
    for b = 250; b < 256; b++ {
            fmt.Printf("%d %c\n", b, b)
    }

    ../main.go:2:17: constant 256 overflows byte

One solution is to use a wider data type, such as an `int`:

    for i := 250; i < 256; i++ {
            fmt.Printf("%d %c\n", i, i)
    }

    250 ú
    251 û
    252 ü
    253 ý
    254 þ
    255 ÿ

Another option is to put the termination test at the end of the loop:

    for b := byte(250); ; b++ {
            fmt.Printf("%d %c\n", b, b)
            if b == 255 {
                    break
            }
    }

    250 ú
    251 û
    252 ü
    253 ý
    254 þ
    255 ÿ

<a href="gotcha-bitwise-operators.html" class="prev"></a>

« Prev

Why does Go and Pythagoras disagree?

[](go-gotcha.html#toc)

TOC

Go gotcha

16 of 26

<a href="gotcha-octal-decimal-hexadecimal-literal.html" class="next"></a>

Next »

Numbers that start with zero

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
