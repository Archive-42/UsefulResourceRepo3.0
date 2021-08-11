<span class="underline"></span>

<span class="underline"></span>

Further Reading
---------------

[Function literals and closures](anonymous-function-literal-lambda-closure.html)  
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

Go: Function types and values
=============================

Functions in Go are first class citizens. Function types and function values can be used and passed around just like other values.

    type Operator func(x float64) float64

    // Map applies op to each element of a.
    func Map(op Operator, a []float64) []float64 {
            res := make([]float64, len(a))
            for i, x := range a {
                    res[i] = op(x)
            }
            return res
    }

    func main() {
            op := math.Abs
            a := []float64{1, -2}
            b := Map(op, a)
            fmt.Println(b) // [1 2]

            c := Map(func(x float64) float64 { return 10 * x }, b)
            fmt.Println(c) // [10, 20]
    }

The second call to `Map` uses an **anonymous function** (or **lambda**). See [Function literals and closures](anonymous-function-literal-lambda-closure.html) for more about lambdas in Go.

Details
-------

A function type describes the set of all functions with the same parameter and result types.

-   The value of an uninitialized variable of function type is `nil`.
-   The parameter names are optional. The following two function types are **identical**:

        func(x, y int) int

        func(int, int) int

Comments (1)
------------

![User avatar](https://www.gravatar.com/avatar/d41d8cd98f00b204e9800998ecf8427e?d=mp)

concise and to the point. thanks!

<span style="color: grey">by Anonymous | </span> <span class="reply-button">Reply</span>

### Add comment

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
