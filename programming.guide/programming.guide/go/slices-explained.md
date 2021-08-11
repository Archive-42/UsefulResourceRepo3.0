## Further Reading

[Append function explained](append-explained.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Copy function explained](copy-explained.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Delete an element from a slice](delete-element-slice.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Clear a slice](clear-slice.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Go Slices: usage and internals](https://blog.golang.org/go-slices-usage-and-internals)  
<span style="color: grey; font-style: italic; font-size: smaller">The Go Blog</span>

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

# Go: Slices explained

A slice is a view of an underlying array. You can use `s[i]` to view and modify an element of a slice `s`. Modifications will affect the underlying array as well.

You may think of a slice as a **descriptor of an array segment**:

- passing a slice as argument to a method does not cause the data to be copied (as with arrays),
- and a slice can grow and shrink within the bounds of the underlying array.

## Create

The type of a slice is `[]T`. Here's a simple way to declare and initialize a slice:

    s := []string{"foo", "bar", "baz", "qux"}

Here's how to use the [`make`](make-slice-map-channel.html) function to create and initialize a slice with five zeroes:

    s := make([]int, 5)

You can also create a slice backed by an existing array.

a := \[...\]int{0, 1, 2, 3, 4, 5} s1 := a\[1:4\] 0 1 2 3 4 5 s2 := a\[:4\] 0 1 2 3 4 5 s3 := a\[4:\] 0 1 2 3 4 5 s4 := a\[:\] 0 1 2 3 4 5

## Length and capacity

0 1 2 3 4 5 6 7 8 9 length capacity

The **length** and **capacity** can be retrieved using the built-in functions [`len`](https://golang.org/pkg/builtin/#len) and [`cap`](https://golang.org/pkg/builtin/#cap).

The [`make`](https://golang.org/pkg/builtin/#make) function optionally takes a capacity as a third argument. `make([]int, 10, 100)` for example, is the same as `new([100]int)[:10]`.

## Reslice and extend

You can slice a slice:

// Create slice s := a\[1:5\] 0 1 2 3 4 5 // Slice again! s = s\[1:3\] 0 1 2 3 4 5

The indices in the last line are relative to the slice itself, not to the backing array. The end index is not bound by the slice's length, but by it's the **capacity**, which means we can **extend the slices length**:

// Create slice s := a\[1:3\] 0 1 2 3 4 5 // Extend length s = s\[0:4\] 0 1 2 3 4 5

Trying to extend beyond the capacity will cause a panic. You can not use a negative start index.

## Append

There's a built-in function called [`append`](append-explained.html) which appends elements to a slice. It will automatically allocate a larger backing array if the capacity is exceeded.

s := make(\[\]int, 0, 3) 0 0 0 s = append(s, 1) 1 0 0 s = append(s, 2) 1 2 0 s = append(s, 3, 4, 5) 1 2 3 4 5 0 0 0

## Zero value

The default value of a slice is `nil`. The functions `len`, `cap` and `append` all regard `nil` as an empty slice with 0 capacity.

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
