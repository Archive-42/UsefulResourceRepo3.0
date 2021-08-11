## Further Reading

[int vs. int64](int-vs-int64.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Numeric types](https://golang.org/ref/spec#Numeric_types)  
<span style="color: grey; font-style: italic; font-size: smaller">The Go Programming Language Specification</span>

## Top Go Articles

1.  [Go gotcha](go-gotcha.html)
2.  [String handling cheat sheet](string-functions-reference-cheat-sheet.html)
3.  [Maps explained](maps-explained.html)
4.  [For loops explained](for-loop.html)
5.  [Concurrent programming](go-concurrency-tutorial.html)

[**See all 197 Go articles**](index.html)

## Top Algorithm Articles

1.  [Dynamic programming vs memoization vs tabulation](../dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](../big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](../sliding-window-example.html)
4.  [What makes a good loop invariant?](../what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](../random-point-within-circle.html)

[**See all articles**](../index.html)

# Go: What’s the maximum value of an int?

Go has two predeclared integer types with implementation-specific sizes:

- a `uint` has either 32 or 64 bits;
- an `int` has the same size as a `uint`.

This code computes the limit values as **untyped constants**:

    const BitsPerWord = 32 << (^uint(0) >> 63) // either 32 or 64

    const (
            MaxInt  = 1<<(BitsPerWord-1) - 1 // either (1<<31)-1 or (1<<63)-1
            MinInt  = -MaxInt - 1            // either -1<<31 or -1<<63
            MaxUint = 1<<BitsPerWord - 1     // either (1<<32)-1 or (1<<64)-1
    )

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
