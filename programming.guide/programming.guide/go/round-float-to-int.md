## Further Reading

[Conversions](conversions.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Print with fmt cheat sheet](fmt-printf-reference-cheat-sheet.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[The trouble with rounding floating point numbers](https://www.theregister.co.uk/2006/08/12/floating_point_approximation/)  
<span style="color: grey; font-style: italic; font-size: smaller">The Register</span>

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

# Go: Round float to integer value

- [Round away from zero](round-float-to-int.html#round-away-from-zero)
- [Round to an even number](round-float-to-int.html#round-to-an-even-number)
- [Convert to an int type](round-float-to-int.html#convert-to-an-int-type)
- [Before Go 1.10](round-float-to-int.html#before-go-110)

## Round away from zero

Use [`math.Round`](https://tip.golang.org/pkg/math/#Round), which will be introduced in [**Go 1.10**](https://tip.golang.org/doc/go1.10), to return the nearest integer, rounding ties away from zero.

    for _, x := range []float64{-0.6, -0.4, 0.4, 0.6} {
            fmt.Println(math.Round(x))
    }

    -1
    -0
    0
    1

Note the special cases:

    Round(±0) = ±0
    Round(±Inf) = ±Inf
    Round(NaN) = NaN

## Round to an even number

Use [`math.RoundToEven`](https://tip.golang.org/pkg/math/#RoundToEven), which will be introduced in [**Go 1.10**](https://tip.golang.org/doc/go1.10), to return the nearest integer, rounding ties to an even number.

    fmt.Println(math.RoundToEven(0.5), math.RoundToEven(1.5))
    // Output: 0 2

## Convert to an int type

Note that when converting a floating-point number to an `int` type, the fraction is discarded (truncation towards zero):

    var f float64 = 1.9
    n := int64(f) //  1
    n = int64(-f) // -1

**Warning:** If the result type cannot represent the value the conversion succeeds but the result is implementation-dependent.

## Before Go 1.10

The following implementations are equivalent to [`math.Round`](https://tip.golang.org/pkg/math/#Round) and [`math.RoundToEven`](https://tip.golang.org/pkg/math/#RoundToEven), but less efficient.

`Round` returns the nearest integer, rounding ties away from zero.

    func Round(x float64) float64 {
            t := math.Trunc(x)
            if math.Abs(x-t) >= 0.5 {
                    return t + math.Copysign(1, x)
            }
            return t
    }

`RoundToEven` returns the nearest integer, rounding ties to an even number.

    func RoundToEven(x float64) float64 {
            t := math.Trunc(x)
            odd := math.Remainder(t, 2) != 0
            if d := math.Abs(x - t); d > 0.5 || (d == 0.5 && odd) {
                    return t + math.Copysign(1, x)
            }
            return t
    }

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
