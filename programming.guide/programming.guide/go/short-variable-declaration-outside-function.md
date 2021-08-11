



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

# Go: Variable declaration outside of function body

As you may have noticed, programs with short variable declarations outside a function do not compile:

    package main

    n := 1    // does not compile

    func main() {}

    ../main.go:3:1: syntax error: non-declaration statement outside function body

Short variable declarations can only be used inside functions. You have to write:

    package main

    var n = 1   // does compile

    func main() {}

This is a trade-off in the design of the Go language:

> At the top level, every declaration begins with a keyword. This simplifies parsing. <a href="https://groups.google.com/forum/#!msg/golang-nuts/qTZemuGDV6o/IyCwXPJsUFIJ" class="quote-source">golang-nuts forum: Ian Lance Taylor</a>

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
