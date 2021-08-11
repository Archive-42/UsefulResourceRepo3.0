<span class="underline"></span>

<span class="underline"></span>

## Related

[Compute min and max](max-min-function.html)  
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

# Go: Compute absolute values

## Integers

Go has no built-in library function for computing the absolute value of an integer. It's simple to write your own.

    func Abs(x int32) int32 {
            if x < 0 {
                    return -x
            }
            return x
    }

**Warning:** The smallest value of a signed integer type doesn't have a corresponding positive value. For example

- `math.MinInt32` equals -214748364**8**, while
- `math.MaxInt32` equals 214748364**7**.

There's no good way to deal with this. In fact, `Abs` returns a **negative value** in this case:

    fmt.Println(Abs(math.MinInt32)) // Output: -2147483648

The C and Java standard libraries also behave like this.

## Floats

Use [`math.Abs`](https://golang.org/pkg/math/#Abs) to compute the absolute value of a floating-point number:

    // Abs returns the absolute value of x.
    func Abs(x float64) float64

Note the special cases:

    Abs(±Inf) = +Inf
    Abs(NaN) = NaN

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
