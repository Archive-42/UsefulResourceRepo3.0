



## Further Reading

[Interfaces explained](interfaces-explained.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[The io.Reader interface](io-reader-interface-explained.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Generating code](https://blog.golang.org/generate)  
<span style="color: grey; font-style: italic; font-size: smaller">The Go Blog</span>

[Reducing boilerplate with go generate](https://blog.gopheracademy.com/advent-2015/reducing-boilerplate-with-go-generate/)  
<span style="color: grey; font-style: italic; font-size: smaller">Gopher Academy Blog</span>

[Type assertions and type switches](type-assertion-switch.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[The Laws of Reflection](https://blog.golang.org/laws-of-reflection)  
<span style="color: grey; font-style: italic; font-size: smaller">The Go Blog</span>

[Experience Reports: Generics](https://github.com/golang/go/wiki/ExperienceReports#generics)  
<span style="color: grey; font-style: italic; font-size: smaller">The Go Wiki</span>

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

# Go: Generics (alternatives and workarounds)

Go has some built-in generic data types, such as slices and maps, and generic functions, such as `append` and `copy`. However, there is no mechanism for writing your own generic functions.

Here are some techniques that can be used in place of parametric polymorphism in Go.

## Find a well-fitting interface

Describe the generic behaviour of your data with an interface.

The [`io.Reader`](https://golang.org/pkg/io/#Reader) interface, which represents the read end of a stream of data, is a good example: - many functions take an [`io.Reader`](https://golang.org/pkg/io/#Reader) as input, - and many data types, including files, network connections, and ciphers, implement this interface.

## Use multiple functions

If you only need to support a few data types, consider offering a seperate function for each type.

As an example, the two packages [`strings`](https://golang.org/pkg/strings/) and [`bytes`](https://golang.org/pkg/bytes/) come with pretty much the same set of functions.

If this leads to an unmanageable amount of copy and paste, consider using a code generation tool, such as [go generate](https://golang.org/cmd/go/#hdr-Generate_Go_files_by_processing_source).

## Use the empty interface

If little is known about the data, consider using the empty interface `interface{}` in combination with type assertions and reflection. Libraries such as [`fmt`](https://golang.org/pkg/fmt/) and [`encoding/json`](https://golang.org/pkg/encoding/json/) couldn't have been written in any other way.

## Write an experience report

If none of these solutions are effective, consider submitting an experience report:

> This page collects experience reports about problems with Go that might inform our design of solutions to those problems. These reports should focus on the problems: they should not focus on and need not propose solutions.
>
> We hope to use these experience reports to understand where people are having trouble writing Go, to help us prioritize future changes to the Go ecosystem. <a href="https://github.com/golang/go/wiki/ExperienceReports" class="quote-source">The Go Wiki: Experience Reports</a>

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
