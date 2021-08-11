## Further Reading

[Slices explained](slices-explained.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

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

# Go: Empty slice vs. nil slice

In practice, **nil slices** and **empty slices** can often be treated in the same way:

- they have zero length and capacity,
- they can be used with the same effect in for loops and append functions,
- and they even look the same when printed.

<!-- -->

    var a []int = nil
    fmt.Println(len(a)) // 0
    fmt.Println(cap(a)) // 0
    fmt.Println(a)      // []

However, if needed, you can tell the difference:

    var a []int = nil
    var a0 []int = make([]int, 0)

    fmt.Println(a == nil)  // true
    fmt.Println(a0 == nil) // false

    fmt.Printf("%#v\n", a)  // []int(nil)
    fmt.Printf("%#v\n", a0) // []int{}

The official Go wiki recommends using nil slices over empty slices:

> \[…\] the nil slice is the preferred style.
>
> Note that there are limited circumstances where a non-nil but zero-length slice is preferred, such as when encoding JSON objects (a nil slice encodes to `null`, while `[]string{}` encodes to the JSON array `[]`).
>
> When designing interfaces, avoid making a distinction between a nil slice and a non-nil, zero-length slice, as this can lead to subtle programming errors. <a href="https://github.com/golang/go/wiki/CodeReviewComments#declaring-empty-slices" class="quote-source">The Go wiki: Declaring empty slices</a>

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
