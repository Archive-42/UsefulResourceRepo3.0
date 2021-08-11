



## Related

[Unused local variables](unused-local-variables.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Unused imports](unused-imports.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Command goimports](https://godoc.org/golang.org/x/tools/cmd/goimports)  
<span style="color: grey; font-style: italic; font-size: smaller">GoDoc</span>

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

# Go: Blank identifier (underscore)

The **blank identifier** `_` is an anonymous placeholder. It may be used like any other identifier in a declaration, but it does not introduce a binding.

## Ignore values

The blank identifier provides a way to ignore left-hand side values in an assignment:

    _, present := timeZone["CET"]

    sum := 0
    for _, n := range a {
            sum += n
    }

## Import for side effects

It can also be used to import a package solely for its side effects:

    import _ "image/png" // init png decoder function

## Silence the compiler

It can be used to during development to avoid compiler errors about unused imports and variables in a half-written program:

    package main

    import (
            "fmt"
            "log"
            "os"
    )

    var _ = fmt.Printf // DEBUG: delete when done

    func main() {
            f, err := os.Open("test.go")
            if err != nil {
                    log.Fatal(err)
            }
            _ = f // TODO: read file
    }

For an automatic solution, use the [goimports](https://godoc.org/golang.org/x/tools/cmd/goimports) tool, which rewrites a Go source file to have the correct imports. Many Go editors and IDEs run this tool automatically.

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
