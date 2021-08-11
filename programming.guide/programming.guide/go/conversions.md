<span class="underline"></span>

<span class="underline"></span>

## Further Reading

[Convert int to string](convert-int-to-string.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Format a time or date](format-parse-string-time-date-example.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Untyped numeric constants with no limits](untyped-constants.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

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

# Go: Conversions

The expression `T(x)` converts the value `x` to the type `T`.

    f := 5.1
    i := int(f) // convert float to int

The conversion rules are extensive but predictable:

- all conversions between typed expressions must be explicitly stated,
- and illegal conversions are caught by the compiler.

Conversions between numbers and strings may **change the representation** and have a **run-time cost**. All other conversions only change the type but not the representation of `x`.

## Integers

- When converting to a shorter integer type, the value is **truncated** to fit in the result type's size.
- When converting to a longer integer type,
  - if the value is a signed integer, it is [**sign extended**](https://en.wikipedia.org/wiki/Sign_extension);
  - otherwise it is **zero extended**.

<!-- -->

    var a uint16 = 0x10fe //  bit pattern: 0001 0000 1111 1110

    // Truncation
    b := int8(a) // -2        bit pattern:           1111 1110

    // Sign extention
    c := uint16(b) // 0xfffe  bit pattern: 1111 1111 1111 1110

## Floats

- When converting a floating-point number to an integer, the **fraction is discarded** (truncation towards zero).
- When converting an integer or floating-point number to a floating-point type, the result value is **rounded to the precision** specified by the destination type.

<!-- -->

    var f float64 = 1.9
    n := int64(f) // 1
    n = int64(-f) // -1

    n = 1234567890
    g := float32(n) // 1.234568e+09

**Warning:** In all non-constant conversions involving floating-point or complex values, if the result type cannot represent the value the conversion succeeds but the result value is implementation-dependent. <a href="https://golang.org/ref/spec#Conversions" class="quote-source">The Go Programming Language Specification: Conversions</a>

## Integer to string

- When converting an integer to a string, the value is interpreted as a Unicode code point, and the resulting string will contain the character represented by that code point, encoded in UTF-8.
- If the value does not represent a valid code point (for instance if it's negative), the result will be `"\ufffd"`, the Unicode replacement character �.

<!-- -->

    string(97) // "a"
    string(-1) // "\ufffd" == "\xef\xbf\xbd"

To get the decimal string representation of an integer, use the [`strconv.Itoa`](https://golang.org/pkg/strconv/#Itoa) function:

    strconv.Itoa(97) // "97"

## Strings and byte slices

- Converting a slice of bytes to a string type yields a string whose successive bytes are the elements of the slice.
- Converting a value of a string type to a slice of bytes type yields a slice whose successive elements are the bytes of the string.

<!-- -->

    string([]byte{97, 230, 151, 165}) // "a日"
    []byte("a日")                     // []byte{97, 230, 151, 165}

## Strings and rune slices

- Converting a slice of runes to a string type yields a string that is the concatenation of the individual rune values converted to strings.
- Converting a value of a string type to a slice of runes type yields a slice containing the individual Unicode code points of the string.

<!-- -->

    string([]rune{97, 26085}) // "a日"
    []rune("a日")             // []rune{97, 26085}

## Underlying type

A non-constant value can be converted to type `T` if it has the same underlying type as `T`.

In this example, the underlying type of `int64`, `T1`, and `T2` is `int64`.

    type (
            T1 int64
            T2 T1
    )

It's idiomatic in Go to convert the type of an expression to access a specific method:

    var n int64 = 12345
    fmt.Println(n)                // 12345
    fmt.Println(time.Duration(n)) // 12.345µs

(The underlying type of [`time.Duration`](https://golang.org/pkg/time/#Duration) is `int64`, and the `time.Duration` type has a [`String`](https://golang.org/pkg/time/#Duration.String) method that returns the duration formatted as a time.)

## Implicit conversions

The only implicit conversion in Go is when an untyped constant (see [Go: Untyped numeric constants with no limits](untyped-constants.html)) is used in a situation where a type is required.

In this example the untyped literals `1` and `2` are implicitly converted:

    var f float64
    f = 1 // Same as: f = float64(1)

    t := 2 * time.Second // Same as: t := time.Duration(2) * time.Second

(The implicit conversions are necessary since there is no mixing of numeric types in Go. You can only multiply a `time.Duration` with another `time.Duration`.)

When the type can't be inferred from the context, an untyped constant is converted to a `bool`, `int`, `float64`, `complex128`, `string` or `rune` depending on the syntactical format of the constant:

    n := 1   // Same as: n := int(1)
    f := 1.0 // Same as: f := float64(1.0)
    s := "A" // Same as: s := string("A")
    c := 'A' // Same as: c := rune('A')

Illegal implicit conversions are caught by the compiler:

    var b byte = 256 // Same as: var b byte = byte(256)

    ../main.go:2:6: constant 256 overflows byte

## Pointers

The Go compiler does not allow conversions between pointers and integers. The package [`unsafe`](https://golang.org/pkg/unsafe/) implements this functionality under restricted circumstances.

The built-in package unsafe, known to the compiler, provides facilities for low-level programming including operations that violate the type system. A package using unsafe must be vetted manually for type safety and may not be portable. <a href="https://golang.org/ref/spec#Package_unsafe" class="quote-source">The Go Programming Language Specification: Package unsafe</a>

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
