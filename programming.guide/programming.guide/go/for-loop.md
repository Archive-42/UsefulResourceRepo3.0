<span class="underline"></span>

<span class="underline"></span>

Further Reading
---------------

[Range loops (for each loops) explained](for-loop-range-array-slice-map-channel.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Iterator pattern](iterator-generator-pattern.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[do-while loop](do-while-loop.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

Top Go Articles
---------------

1.  [Go gotcha](go-gotcha.html)
2.  [String handling cheat sheet](string-functions-reference-cheat-sheet.html)
3.  [Maps explained](maps-explained.html)
4.  For loops explained
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

Go: For loops explained
=======================

-   [Three-component loop](for-loop.html#three-component-loop)
-   [While loop](for-loop.html#while-loop)
-   [Infinite loop](for-loop.html#infinite-loop)
-   [For each loop](for-loop.html#for-each-loop)
-   [Exit a loop](for-loop.html#exit-a-loop)

Three-component loop
--------------------

    sum := 0
    for i := 1; i < 5; i++ {
            sum += i
    }
    fmt.Println(sum) // 10 (1+2+3+4)

This version of the Go for loop works just as in C/Java/JavaScript.

1.  The init statement, `i := 0`, runs.
2.  The condition, `i < 5`, is evaluated.
3.  If it's true, the loop body executes,
4.  otherwise the loop terminates.
5.  The post statement, `i++`, executes.
6.  Back to step 2.

The scope of `i` is limited to the loop.

While loop
----------

If the init and post statements are omitted, the Go `for` loop behaves like a C/Java/JavaScript while loop:

    power := 1
    for power < 5 {
            power *= 2
    }
    fmt.Println(power) // 8 (1*2*2*2)

1.  The condition, `i < 5`, is evaluated.
2.  If it's true, the loop body executes,
3.  otherwise the loop terminates.
4.  Back to step 1.

Infinite loop
-------------

By also leaving out the condition, you get an infinite loop.

    sum := 0
    for {
            sum++ // repeated forever
    }
    fmt.Println(sum) // unreachable

For each loop
-------------

Looping over elements in slices, arrays, maps, channels and strings is often better done using the `range` keyword:

    strings := []string{"hello", "world"}
    for i, s := range strings {
            fmt.Println(i, s)
    }

    0 hello
    1 world

For more examples, see [Range loops (for each loops) explained](for-loop-range-array-slice-map-channel.html).

Exit a loop
-----------

The `break` and `continue` keywords work just as they do in C/Java/JavaScript.

    sum := 0
    for i := 1; i < 5; i++ {
            if i%2 != 0 { // skip odd numbers
                    continue
            }
            sum += i
    }
    fmt.Println(sum) // 6 (2+4)

-   A `continue` statement begins the next iteration of the innermost `for` loop at its post statement.
-   A `break` statement terminates execution of the innermost `for`, `switch`, or `select` statement.

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
