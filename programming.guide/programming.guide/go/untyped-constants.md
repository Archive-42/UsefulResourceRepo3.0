<span class="underline"></span>

<span class="underline"></span>

## Further Reading

[Constants](https://blog.golang.org/constants)  
<span style="color: grey; font-style: italic; font-size: smaller">The Go Blog</span>

[Constants](https://tour.golang.org/basics/15)  
<span style="color: grey; font-style: italic; font-size: smaller">A Tour of Go</span>

[Constants](https://golang.org/ref/spec#Constants)  
<span style="color: grey; font-style: italic; font-size: smaller">The Go Programming Language Specification</span>

[Enumeration (enum) with string representation](define-enumeration-string.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[iota](iota.html)  
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

# Go: Untyped numeric constants with no limits

Constants may be **typed** or **untyped**.

    const a uint = 17
    const b = 55

An untyped constant has **no limits**. When it's used in a context that requires a type, a type will be inferred and a limit applied.

    // Too big for an int
    const big = 10000000000

    // Still ok: "untyped = untyped * untyped"
    const bigger = big * 100

    // No problem: Result fits in an int
    var i int = big / 100

    // Compile time error: "constant 10000000000 overflows int"
    var j int = big

The inferred type is determined by the syntax of the value. `123` for instance gets type `int` and `123.4` becomes a `float64`. The other possibilities are `rune` (alias for `int32`) and `complex128`.

## Enumerations

Go does not have enumerated types. Instead, you can use the special name `iota` in a single `const` declaration to get a series of increasing values. When an initialization expression is omitted for a `const`, it reuses the preceding expression.

    const (
        red = iota  // red == 0
        blue        // blue == 1
        green       // green == 2
    )

The article [Define an enumeration (enum) with a string representation](define-enumeration-string.html) has a detailed example.

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
