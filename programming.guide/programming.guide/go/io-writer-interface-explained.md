<span class="underline"></span>

<span class="underline"></span>

Related
-------

[The io.Reader interface](io-reader-interface-explained.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Go Walkthrough: io package](https://medium.com/go-walkthrough/go-walkthrough-io-package-8ac5e95a9fbd)  
<span style="color: grey; font-style: italic; font-size: smaller">by Ben Johnson</span>

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

Go: The io.Writer interface
===========================

The [`io.Writer`](https://golang.org/pkg/io/#Writer) interface represents an entity to which you can write a stream of bytes:

    type Writer interface {
            Write(p []byte) (n int, err error)
    }

`Write` writes up to `len(p)` bytes from `p` to the underlying data stream; it returns the number of bytes written and any error encountered that caused the write to stop early.

Example
-------

The standard library provides many Writer [implementations](https://golang.org/search?q=Write#Global), and Writers are accepted as input by many utilities.

For example, since [`bytes.Buffer`](https://golang.org/pkg/bytes/#Buffer) has a `Write` method you can write directly into the buffer using [`fmt.Fprintf`](https://golang.org/pkg/fmt/#Fprintf):

    var buf bytes.Buffer
    fmt.Fprintf(&buf, "Size: %d MB.", 85)
    str := buf.String()) // str == "Size: 85 MB."

Optimizing string writes
------------------------

Some Writers in the standard library have an additional `WriteString` method. This method can be more efficient than the standard `Write` method since it writes a string directly without allocating a byte slice.

You can take direct advantage of this optimization by using the [`io.WriteString()`](https://golang.org/pkg/io/#WriteString) function:

    func WriteString(w Writer, s string) (n int, err error)

If `w` implements a `WriteString` method, it is invoked directly. Otherwise, `w.Write` is called exactly once.

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
