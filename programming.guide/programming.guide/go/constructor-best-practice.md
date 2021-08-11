



## Further Reading

[Inheritance and object-oriented programming](inheritance-object-oriented.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Default value of struct, string, slice, map](default-zero-value.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Public vs. private](public-private.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Constructors and composite literals](https://golang.org/doc/effective_go.html#composite_literals)  
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

# Go: Constructors

Go doesn't have explicit constructors. The idiomatic way to set up new data structures is to use proper **zero values** coupled with **factory functions**.

## Zero value

Try to make the default [**zero value**](default-zero-value.html) useful and document its behavior. Sometimes this is all that's needed:

    // A StopWatch is a simple clock utility.
    // Its zero value is an idle clock with 0 total time.
    type StopWatch struct {
            start   time.Time
            total   time.Duration
            running bool
    }

- `StopWatch` takes advantage of the useful zero values of `time.Time`, `time.Duration` and `bool`.
- In turn, users of `StopWatch` can benefit from _its_ useful zero value.

<!-- -->

    var clock StopWatch // Ready to use, no initialization needed.

## Factory

If the zero value doesn't suffice, use factory functions named `NewFoo` or just `New`:

    scanner := bufio.NewScanner(os.Stdin)
    err := errors.New("Houston, we have a problem")

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
