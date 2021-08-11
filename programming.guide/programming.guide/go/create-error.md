<span class="underline"></span>

<span class="underline"></span>

Further reading
---------------

[Error handling and Go](https://blog.golang.org/error-handling-and-go)  
<span style="color: grey; font-style: italic; font-size: smaller">The Go Blog</span>

Error handling
--------------

1.  [Errors explained](errors-explained.html)
2.  Create a custom error
3.  [Panic explained](panic-explained.html)
4.  [Recover from a panic](recover-from-panic.html)
5.  [Stack traces](stack-trace.html)

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

Go: Create a custom error
=========================

First, two out-of-the-box options:

    // Simple string-based error:
    err1 := errors.New("Houston, we have a problem")

    // With formatting:
    err2 := fmt.Errorf("%d errors, %d warnings", errCount, warnCount)

Custom errors with data
-----------------------

All you need to do is satisfy the predeclared [`error`](https://golang.org/ref/spec/#Errors) interface:

    type error interface {
        Error() string
    }

**Example:** Here's a `SyntaxError` with line and position:

    type SyntaxError struct {
            Line int
            Col  int
    }

    func (e *SyntaxError) Error() string {
            return fmt.Sprintf("%d:%d: Syntax error",
                    e.Line, e.Col)
    }

You create it as follows:

    err := &SyntaxError{
            Line: 17,
            Col:  55,
    }

Let's do another one:

**Example:** Here's an `InternalError`:

    type InternalError struct {
            Path string
    }

    func (e *InternalError) Error() string {
            return fmt.Sprintf("parse %v: internal error", e.Path)
    }

Handling the errors
-------------------

Suppose `RiskyFunction` may return a `SyntaxError` or an `InternalError`. Here's how you would handle the two cases:

    if err := RiskyFunction(); err != nil {
            switch e := err.(type) {
            case *SyntaxError:
                    // Do something interesting with e.Line and e.Col.
            case *InternalError:
                    // Abort and file an issue.
            default:
                    log.Println(e)
            }
    }

<a href="errors-explained.html" class="prev"></a>

« Prev

Errors explained

[](go-errors-tutorial.html)

TOC

Error handling

2 of 5

<a href="panic-explained.html" class="next"></a>

Next »

Panic explained

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
