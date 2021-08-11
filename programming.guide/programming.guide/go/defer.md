<span class="underline"></span>

<span class="underline"></span>

Further Reading
---------------

[Defer statements](https://golang.org/ref/spec#Defer_statements)  
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

Go: Defer statement
===================

A deferred method call is executed just before leaving the surrounding function.

**Example:** Executed before normal return:

    func main() {
            defer fmt.Println("World")
            fmt.Println("Hello")
    }

Output:

    Hello
    World

Deferred calls are executed even when the function panics.

**Example:** Executed during panic:

    func main() {
            defer fmt.Println("World")
            panic("Eeek")
            fmt.Println("Hello")
    }

Output:

    World
    panic: Eeek

    <stack trace...>

A deferred function's arguments are evaluated when the defer statement executes.

Deferred function calls are executed in last-in-first-out order.

**Example:** Three deferred calls:

    func main() {
            fmt.Println("start")
            for i := 1; i <= 3; i++ {
                    defer fmt.Println(i)
            }
            fmt.Println("end")
    }

Output:

    start
    end
    3
    2
    1

Deferred functions may access and modify the surrounding function's named return parameters:

**Example:** Change return value at the very last moment:

    func Foo() (result int) {
            defer func() {
                    result = 7
            }()
            return 0
    }

`Foo()` returns 7.

Clean-up
--------

Defer is commonly used to perform clean-up actions, such as closing a file or unlocking a mutex.

**Example:** Here defer statements are used to ensure that all files are closed before leaving the `CopyFile` function, whichever way that happens.

    func CopyFile(dstName, srcName string) (written int64, err error) {
            src, err := os.Open(srcName)
            if err != nil {
                    return
            }
            defer src.Close()

            dst, err := os.Create(dstName)
            if err != nil {
                    return
            }
            defer dst.Close()

            return io.Copy(dst, src)
    }

Recover from panic
------------------

The article [**Recover from a panic**](recover-from-panic.html) demonstrates how to use a defer statement when recovering from a panic.

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
