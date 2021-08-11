<span class="underline"></span>

<span class="underline"></span>

## Related

[Command go](https://golang.org/cmd/go/)  
<span style="color: grey; font-style: italic; font-size: smaller">The Go Programming Language</span>

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

# Go: Find build version

    fmt.Println(runtime.Version())

The function [`runtime.Version`](https://golang.org/pkg/runtime/#Version) returns the Go tree's version string, which is

- either the commit hash and date at the time of the build,
- or, when possible, a release tag like `go1.9`.

<!-- -->

    $ go version

The command [`go version`](https://golang.org/cmd/go/#hdr-Print_Go_version) prints the version in the same format as `runtime.Version`.

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
