<span class="underline"></span>

<span class="underline"></span>

## Further Reading

[Range loops (for each loops) explained](for-loop-range-array-slice-map-channel.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Function types and values](function-pointer-type-declaration.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Iterators in Go](https://ewencp.org/blog/golang-iterators/)  
<span style="color: grey; font-style: italic; font-size: smaller">by Ewen Cheslack-Postava</span>

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

# Go: Iterator pattern

Go has built-in range loops for iterating over slices, arrays, strings, maps and channels. See [Range loops explained](for-loop-range-array-slice-map-channel.html).

To iterate over other types of data, an iterator function with callbacks is a clean and fairly efficient abstraction.

## Basic iterator pattern

    // Iterate calls the f function with n = 1, 2, and 3.
    func Iterate(f func(n int)) {
            for i := 1; i <= 3; i++ {
                    f(i)
            }
    }

In use:

    Iterate(func(n int) { fmt.Println(n) })

    1
    2
    3

## Iterator with break

    // Iterate calls the f function with n = 1, 2, and 3.
    // If f returns true, Iterate returns immediately
    // skipping any remaining values.
    func Iterate(f func(n int) (skip bool)) {
            for i := 1; i <= 3; i++ {
                    if f(i) {
                            return
                    }
            }
    }

In use:

    Iterate(func(n int) (skip bool) {
            fmt.Println(n)
            return n == 2
    })

    1
    2

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
