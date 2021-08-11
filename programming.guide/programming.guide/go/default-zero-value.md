<span class="underline"></span>

<span class="underline"></span>

## Further Reading

[The zero value](https://golang.org/ref/spec#The_zero_value)  
<span style="color: grey; font-style: italic; font-size: smaller">The Go Programming Language Specification</span>

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

# Go: Default value of struct, string, slice, map

Variables declared without an explicit initial value are set to their **zero values**:

- `false` for booleans,
- `0` for integers,
- `0.0` for floats,
- `""` for strings, and
- `nil` for pointers, functions, interfaces, slices, channels, and maps.

This initialization is done recursively; for example each element of an array of structs will have its fields zeroed if no value is specified.

    var n int // n == 0

    type T struct {
            n int
            f float64
            next *T
    }
    t := new(T) // t.n == 0, t.f == 0.0 and t.next == nil

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
