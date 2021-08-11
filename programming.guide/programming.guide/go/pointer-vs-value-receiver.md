## Further Reading

[Pointers explained](pointers-explained.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Go Code Review Comments: Receiver Type](https://github.com/golang/go/wiki/CodeReviewComments#receiver-type)  
<span style="color: grey; font-style: italic; font-size: smaller">The Go Wiki</span>

[Pointers vs. Values](https://golang.org/doc/effective_go.html#pointers_vs_values)  
<span style="color: grey; font-style: italic; font-size: smaller">Effective Go</span>

[Methods explained](methods-explained.html)  
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

# Go: Pointer vs. value receiver

## Basics

- For a given type, _don't mix_ value and pointer receivers.
- If in doubt, _use pointer receivers_ (they are safe and extendable).

## Pointer receivers

You _must_ use pointer receivers

- if any method needs to mutate the receiver,
- for structs that contain a `sync.Mutex` or similar synchronizing field (they musn't be copied).

You _probably want_ to use pointer receivers

- for large structs or arrays (it can be more efficient),
- in all other cases.

## Value receivers

You _probably want_ to use value receivers

- for `map`, `func` and `chan` types,
- for simple basic types such as `int` or `string`,
- for small arrays or structs that are value types, with no mutable fields and no pointers.

You _may want_ to use value receivers

- for slices with methods that do not reslice or reallocate the slice.

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
