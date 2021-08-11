<span class="underline"></span>

<span class="underline"></span>

Further Reading
---------------

[What’s the maximum value of an int?](max-min-int-uint.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Numeric types](https://golang.org/ref/spec#Numeric_types)  
<span style="color: grey; font-style: italic; font-size: smaller">The Go Programming Language Specification</span>

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

Go: int vs. int64
=================

An `int` is either 32 or 64 bits depending on the platform. The length of an array can always be represented by an `int`.

-   An **index**, a **length** or a **capacity** should normally be an `int`.

-   The types `int8`, `int16`, `int32`, and `int64` are best suited for **data**.  
    When memory isn't an issue, `int64` is often the natural choice.

In this example the data has type `int64`, while the index and the length of the slice has type `int`:

    func Reverse(a []int64) {
            n := len(a)
            for i := 0; i < n/2; i++ {
                    a[i], a[n-i-1] = a[n-i-1], a[i]
            }
    }

Here is an example from the [`time`](https://golang.org/pkg/time/) package:

    // A Duration represents the elapsed time between two instants
    // as an int64 nanosecond count. The representation limits the
    // largest representable duration to approximately 290 years.
    type Duration int64

[**What's the maximum value of an int?**](max-min-int-uint.html) shows how to compute the size and limit values of an `int` as untyped constants.

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
