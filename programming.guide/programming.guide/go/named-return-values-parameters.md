## Further Reading

[Named return values](https://tour.golang.org/basics/7)  
<span style="color: grey; font-style: italic; font-size: smaller">A Tour of Go</span>

[Named result parameters](https://golang.org/doc/effective_go.html#named-results)  
<span style="color: grey; font-style: italic; font-size: smaller">Effective Go</span>

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

# Go: Named return values

In Go return parameters may be **named** and used as regular variables. When the function returns these variables are implicitly used as return values.

    func f() (i int, s string) {
            i = 17
            s = "abc"
            return // same as return i, s
    }

Named return parameters are initialized to their zero values.

The names are not mandatory but can make for good documentation. Correctly used, named return parameters can also help to clarify and clean up the code.

This version of [`io.ReadFull`](https://golang.org/pkg/io/#ReadFull), taken from [Effective Go](https://golang.org/doc/effective_go.html#named-results), uses them well:

    func ReadFull(r Reader, buf []byte) (n int, err error) {
        for len(buf) > 0 && err == nil {
            var nr int
            nr, err = r.Read(buf)
            n += nr
            buf = buf[nr:]
        }
        return
    }

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
