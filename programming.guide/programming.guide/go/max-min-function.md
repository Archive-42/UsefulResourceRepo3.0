<span class="underline"></span>

<span class="underline"></span>

Related
-------

[Compute absolute values](absolute-value-int-float.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

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

Go: Compute min and max
=======================

Integers
--------

Go has no built-in min or max library functions for integers. It is simple to write your own:

    // Min returns the smaller of x or y.
    func Min(x, y int) int {
            if x > y {
                    return y
            }
            return x
    }

    // Max returns the larger of x or y.
    func Max(x, y int) int {
            if x < y {
                    return y
            }
            return x
    }

Floats
------

For floats, use [`math.Min`](https://golang.org/pkg/math/#Min) and [`math.Max`](https://golang.org/pkg/math/#Max) from the standard library:

    // Min returns the smaller of x or y.
    func Min(x, y float64) float64

    // Max returns the larger of x or y. 
    func Max(x, y float64) float64

Note the special cases:

    Min(x, -Inf) = Min(-Inf, x) = -Inf
    Min(x, NaN) = Min(NaN, x) = NaN
    Min(-0, ±0) = Min(±0, -0) = -0

    Max(x, +Inf) = Max(+Inf, x) = +Inf
    Max(x, NaN) = Max(NaN, x) = NaN
    Max(+0, ±0) = Max(±0, +0) = +0
    Max(-0, -0) = -0

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
