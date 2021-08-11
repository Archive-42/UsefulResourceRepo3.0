



## Further Reading

[Variadic functions (...T)](variadic-function.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Interfaces explained](interfaces-explained.html)  
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

# Go: Optional parameters and method overloading

Go does not have optional parameters, nor does it support method overloading:

> Method dispatch is simplified if it doesn't need to do type matching as well. Experience with other languages told us that having a variety of methods with the same name but different signatures was occasionally useful but that it could also be confusing and fragile in practice. Matching only by name and requiring consistency in the types was a major simplifying decision in Go's type system. <a href="https://golang.org/doc/faq#overloading" class="quote-source">Go FAQ: Why does Go not support overloading of methods and operators?</a>

However, there are [variadic functions](variadic-function.html) (functions that accept a variable number of arguments), and dynamic method dispatch is supported through interfaces. See [Go: Interfaces explained](interfaces-explained.html).

The idiomatic way to emulate optional parameters and method overloading in Go is to write several methods with different names. For example, the [`sort`](https://golang.org/pkg/sort/) package has five different functions for sorting a slice:

- the generic [`sort.Slice`](https://golang.org/pkg/sort/#Slice) and [`sort.SliceStable`](https://golang.org/pkg/sort/#SliceStable),
- and the three more specific [`sort.Float64s`](https://golang.org/pkg/sort/#Float64s), [`sort.Ints`](https://golang.org/pkg/sort/#Ints), and [`sort.Strings`](https://golang.org/pkg/sort/#Strings).

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
