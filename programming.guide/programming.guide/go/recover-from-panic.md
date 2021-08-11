## Related

[Defer statement](defer.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Defer, Panic, and Recover](https://blog.golang.org/defer-panic-and-recover)  
<span style="color: grey; font-style: italic; font-size: smaller">The Go Blog</span>

## Error handling

1.  [Errors explained](errors-explained.html)
2.  [Create a custom error](create-error.html)
3.  [Panic explained](panic-explained.html)
4.  Recover from a panic
5.  [Stack traces](stack-trace.html)

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

# Go: Recover from a panic

A [panic](panic-explained.html) is caused either by a runtime error or an explicit call to the built-in `panic` function.

A program recovers from a panic by calling the built-in function [`recover`](https://golang.org/ref/spec#Handling_panics), after which normal execution is resumed. Since all the functions ordinary code is skipped during a panic, the only chance you have to call `recover` is from within a deferred function.

func foo() { defer bar() statement panic("Argh!") statement statement } func bar() { statement statement recover() statement statement } Return normally

The `recover` function returns whatever you gave as argument to the `panic` function. (During normal operation it will return `nil`.)

## Another example

    func main() {
            s := foo()
            fmt.Printf("main received: %q\n", s)
    }

    func foo() string {
            defer func() {
                    if err := recover(); err != nil {
                            fmt.Printf("recovering from: %q\n", err)
                    }
            }()
            s := "before"
            panic("disaster")
            s += " after"
            return s
    }

Output:

    recovering from: "disaster"
    main received: ""

Since the panic occured before `foo` returned a value, `s` in `main` still has its initial zero value `""`:

## Return a value

To return a value during a panic, use a named return value:

    func main() {
            s := foo()
            fmt.Printf("main received: %q\n", s)
    }

    func foo() (s string) {
            defer func() {
                    if err := recover(); err != nil {
                            fmt.Printf("recovering from: %q\n", err)
                            s += " during"
                    }
            }()
            s = "before"
            panic("disaster")
            s += " after"
            return s
    }

Output:

    recovering from: "disaster"
    main received: "before during"

<a href="panic-explained.html" class="prev"></a>

« Prev

Panic explained

[](go-errors-tutorial.html)

TOC

Error handling

4 of 5

<a href="stack-trace.html" class="next"></a>

Next »

Stack traces

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
