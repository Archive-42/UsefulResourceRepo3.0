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

# Go: Redeclaring variables

As you may have noticed, you can't redeclare a variable which has already been declared in the same block:

    func main() {
            m := 0
            m := 1
            fmt.Println(m)
    }

    ../main.go:3:4: no new variables on left side of :=

You have to write:

    func main() {
            m := 0
            m = 1
            fmt.Println(m)
    }

However, variables can be redeclared in short multi-variable declarations where at least one new variable is introduced:

    func main() {
            m := 0
            m, n := 1, 2
            fmt.Println(m, n)
    }

> Unlike regular variable declarations, a short variable declaration may redeclare variables provided they were originally declared earlier in the same block (or the parameter lists if the block is the function body) with the same type, and at least one of the non-blank variables is new. \[...\]
>
> Redeclaration does not introduce a new variable; it just assigns a new value to the original. <a href="https://golang.org/ref/spec#Short_variable_declarations" class="quote-source">The Go Programming Language Specification: Short variable declarations</a>

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
