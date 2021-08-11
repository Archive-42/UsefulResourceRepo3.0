



## Further Reading

[Why does Go not have exceptions?](https://golang.org/doc/faq#exceptions)  
<span style="color: grey; font-style: italic; font-size: smaller">Go FAQ</span>

## Error handling

1.  Errors explained
2.  [Create a custom error](create-error.html)
3.  [Panic explained](panic-explained.html)
4.  [Recover from a panic](recover-from-panic.html)
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

# Go: Errors explained

Go typically uses return values to indicate errors. Multivalued returns makes it easy to return an error value alongside the normal return value.

The [`os.Open`](https://golang.org/pkg/os/#Open) function is a good example:

    func Open(name string) (file *File, err error)

which is used as follows:

    f, err := os.Open("file.txt")
    if err != nil {
            log.Fatal(err)
    }
    // do something with the open *File f

By convention the built-in `error` type is used:

    type error interface {
        Error() string
    }

The `error` interface requires only an `Error` method, but specific `error` implementations often have additional methods, allowing callers to inspect the details of the error.

To create a simple string-only `error` you can use [`errors.New`](https://golang.org/pkg/errors/#New) as follows:

    if problem {
            return errors.New("Houston, we have a problem")
    }

## Panic

In unrecovorable conditions, due to for instance programming errors, the program can call `panic(err)`. When the program panics, it starts to unwind the call stack. This continues until the stack is empty (at which point the program crashes) or until the `recover` function is called. Calling `panic` is similar to throwing an exception in Java or C++, but instead of try/catch blocks, Go uses deferred methods and the `recover` method.

[](go-errors-tutorial.html)

TOC

Error handling

1 of 5

<a href="create-error.html" class="next"></a>

Next »

Create a custom error

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
