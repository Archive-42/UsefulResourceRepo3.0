<span class="underline"></span>

<span class="underline"></span>

Further reading
---------------

[Blank identifier (underscore)](underscore.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

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

Go: Unused local variables
==========================

As you may have noticed, programs with unused local variables do not compile:

    func main() {
            var n int // "n declared and not used"
            n = 5     // this doesn't help
    }

    ../main.go:2:6: n declared and not used

This is a deliberate feature of the Go language:

> The presence of an unused variable may indicate a bug \[...\] Go refuses to compile programs with unused variables or imports, trading short-term convenience for long-term build speed and program clarity. <a href="https://golang.org/doc/faq#unused_variables_and_imports" class="quote-source">Go FAQ: Can I stop these complaints about my unused variable/import?</a>

Unused global variables and function arguments are however allowed.

Workaround
----------

There's no compiler option to allow unused local variables. If you don't want to remove/comment out the declaration, you can add a dummy assignment:

    func main() {
            var n int
            n = 5
            _ = n  // n is now "used"
    }

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
