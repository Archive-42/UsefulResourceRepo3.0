<span class="underline"></span>

<span class="underline"></span>

## Further Reading

[Defer statement](defer.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Defer, Panic, and Recover](https://blog.golang.org/defer-panic-and-recover)  
<span style="color: grey; font-style: italic; font-size: smaller">The Go Blog</span>

[Run-time panics](https://golang.org/ref/spec#Run_time_panics)  
<span style="color: grey; font-style: italic; font-size: smaller">The Go Programming Language Specification</span>

[Handling panics](https://golang.org/ref/spec#Handling_panics)  
<span style="color: grey; font-style: italic; font-size: smaller">The Go Programming Language Specification</span>

## Error handling

1.  [Errors explained](errors-explained.html)
2.  [Create a custom error](create-error.html)
3.  Panic explained
4.  [Recover from a panic](recover-from-panic.html)
5.  [Stack traces](stack-trace.html)

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

# Go: Panic explained

A program panics by calling the built-in [`panic`](https://golang.org/ref/spec#Handling_panics) function. When it panics, the remaining part of the function is skipped.

statement statement statement panic("Argh!") statement statement statement

Before the function returns, it runs any deferred functions.

func foo() { defer bar() statement panic("Argh!") statement statement } func bar() { statement statement statement statement statement } Return panicking

The stack then unwinds. From the callers perspective it's just as if it had called `panic` itself. In the example below, `baz` calls `qux`, which then panics:

func baz() { statement statement qux() Return panicking statement statement } func qux() { statement statement panic("Argh!") Return panicking statement statement }

The call stack keeps unwinding until the program crashes, or until it recovers from the panic. (The semantics is similar to how exceptions work in Java and C++.)

## Recovering from a panic

A program recovers from a panic by calling the built-in function [`recover`](https://golang.org/ref/spec#Handling_panics), after which normal execution is resumed. Since all the functions ordinary code is skipped during a panic, the only chance you have to call `recover` is from within a deferred function.

func foo() { defer bar() statement panic("Argh!") statement statement } func bar() { statement statement recover() statement statement } Return normally

The `recover` function returns whatever you gave as argument to the `panic` function. (During normal operation it will return `nil`.)

## When to panic?

A function should only panic if it can not handle the situation and it's unlikely that the caller will be able to continue execution. For other types of errors it's idiomatic to use error-indicating return values.

<a href="create-error.html" class="prev"></a>

« Prev

Create a custom error

[](go-errors-tutorial.html)

TOC

Error handling

3 of 5

<a href="recover-from-panic.html" class="next"></a>

Next »

Recover from a panic

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
