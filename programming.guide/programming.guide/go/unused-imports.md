<span class="underline"></span>

<span class="underline"></span>

## Further reading

[Command goimports](https://godoc.org/golang.org/x/tools/cmd/goimports)  
<span style="color: grey; font-style: italic; font-size: smaller">GoDoc</span>

[Blank identifier (underscore)](underscore.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

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

# Go: Unused imports

As you may have noticed, programs with unused imports do not compile:

    package main

    import (
            "fmt"
            "log" // "imported and not used: log"
    )

    func main() {
            fmt.Println("Hello")
    }

    ../main.go:5:2: imported and not used: "log"

This is a deliberate feature of the Go language:

> The presence of an unused variable may indicate a bug \[…\]
>
> Go refuses to compile programs with unused variables or imports, trading short-term convenience for long-term build speed and program clarity. <a href="https://golang.org/doc/faq#unused_variables_and_imports" class="quote-source">Go FAQ: Can I stop these complaints about my unused variable/import?</a>

## Workaround

There's no compiler option to allow unused imports. If you don't want to remove/comment out the import, you can for instance use it in a dummy assignment:

    package main

    import (
            "fmt"
            "log"
    )

    var _ = log.Printf

    func main() {
            fmt.Println("Hello")
    }

## A better solution

Use the [goimports](https://godoc.org/golang.org/x/tools/cmd/goimports) tool, which rewrites a Go source file to have the correct imports. Many Go editors and IDEs run this tool automatically whenever a source file is written.

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
