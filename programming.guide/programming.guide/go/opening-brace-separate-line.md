<span class="underline"></span>

<span class="underline"></span>

## Further Reading

[go fmt your code](https://blog.golang.org/go-fmt-your-code)  
<span style="color: grey; font-style: italic; font-size: smaller">The Go Blog</span>

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

# Go: Opening brace on separate line

As you may have noticed, programs with an opening brace on separate line do not compile:

    func main()
    {
            fmt.Println("Hello")
    }

    ../main.go:1:6: missing function body for "main"
    ../main.go:2:1: syntax error: unexpected semicolon or newline before {

You must write:

    func main() {
            fmt.Println("Hello")
    }

This is a trade-off in the design of the Go language:

> Some have argued that the lexer should do lookahead to permit the brace to live on the next line. We disagree. Since Go code is meant to be formatted automatically by **gofmt**, some style must be chosen. \[...\] The advantages of a single, programmatically mandated format for all Go programs greatly outweigh any perceived disadvantages of the particular style. <a href="https://golang.org/doc/faq#semicolons" class="quote-source">Go FAQ: Why are there braces but no semicolons? And why can't I put the opening brace on the next line?</a>

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
