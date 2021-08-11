



## Further Reading

[Stack Traces in Go](https://www.goinggo.net/2015/01/stack-traces-in-go.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Going Go Programming</span>

## Error handling

1.  [Errors explained](errors-explained.html)
2.  [Create a custom error](create-error.html)
3.  [Panic explained](panic-explained.html)
4.  [Recover from a panic](recover-from-panic.html)
5.  Stack traces

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

# Go: Stack traces

A stack trace is the list of functions that the program was in the middle of when the stack trace was printed.

Stack traces are typically printed to the console when unexpected error occurs. They can be very useful for debugging: - not only do you see where the error happened, - but also how the program arrived in this place.

## Example

    goroutine 11 [running]:
    testing.tRunner.func1(0xc420092690)
            /usr/local/go/src/testing/testing.go:711 +0x2d2
    panic(0x53f820, 0x594da0)
            /usr/local/go/src/runtime/panic.go:491 +0x283
    github.com/yourbasic/bit.(*Set).Max(0xc42000a940, 0x0)
            ../src/github.com/bit/set_math_bits.go:137 +0x89
    github.com/yourbasic/bit.TestMax(0xc420092690)
            ../src/github.com/bit/set_test.go:165 +0x337
    testing.tRunner(0xc420092690, 0x57f5e8)
            /usr/local/go/src/testing/testing.go:746 +0xd0
    created by testing.(*T).Run
            /usr/local/go/src/testing/testing.go:789 +0x2de

The stack trace can be read from the bottom up:

- `testing.(*T).Run` has called `testing.tRunner`
- ...which has called `bit.TestMax`
- ...which has called `bit.(*Set).Max`
- ...which has called `panic`
- ...which has called `testing.tRunner.func1`

The indented lines show the source file and line number at which the function was called. The hexadecimal numbers refer to parameter values, including values of pointers and internal data structures. [Stack Traces in Go](https://www.goinggo.net/2015/01/stack-traces-in-go.html) has more details.

## Print a stack trace

To print the stack trace for the current goroutine, use [`debug.PrintStack`](https://golang.org/pkg/runtime/debug/#PrintStack) from package [`runtime/debug`](https://golang.org/pkg/runtime/debug/).

You can also examine the current stack trace programatically by calling [`runtime.Stack`](https://golang.org/pkg/runtime/#Stack).

## Level of detail

The [`GOTRACEBACK`](https://golang.org/pkg/runtime/#hdr-Environment_Variables) variable controls the amount of output generated when a Go program fails.

- `GOTRACEBACK=none` omits the goroutine stack traces entirely.
- `GOTRACEBACK=single` (the default) prints a stack trace for the current goroutine, eliding functions internal to the run-time system. The failure prints stack traces for all goroutines if there is no current goroutine or the failure is internal to the run-time.
- `GOTRACEBACK=all` adds stack traces for all user-created goroutines.
- `GOTRACEBACK=system` is like `all` but adds stack frames for run-time functions and shows goroutines created internally by the run-time.

<a href="recover-from-panic.html" class="prev"></a>

« Prev

Recover from a panic

[](go-errors-tutorial.html)

TOC

Error handling

5 of 5

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
