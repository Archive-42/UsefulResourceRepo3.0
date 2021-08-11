



## Related

[Slices explained](slices-explained.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Amortized time complexity](../amortized-time-complexity-analysis.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Delete an element from a slice](delete-element-slice.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Copy function explained](copy-explained.html)  
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

# Go: Append function explained

The built-in [`append`](https://golang.org/ref/spec#Appending_and_copying_slices) function appends elements to the end of a slice:

- if there is enough capacity, the underlying array is reused;
- if not, a new underlying array is allocated and the data is copied over.

Append returns the updated slice. Therefore you need to store the result of an append, often in the variable holding the slice itself:

    slice = append(slice, elem1, elem2)
    slice = append(slice, anotherSlice...)

Appending a single element takes constant amortized time. The article [Amortized time complexity](../amortized-time-complexity-analysis.html) explains this in detail.

## Special case

It is legal to append a string to a byte slice:

    slice = append([]byte("hello "), "world"...)

## Examples

**Example:** Append an element to a slice:

    a := []int{1, 2}
    a = append(a, 3) // a == [1 2 3]

**Example:** Concatenate two slices:

    a := []int{1, 2}
    b := []int{11, 22}
    a = append(a, b...) // a == [1 2 11 22]

**Example:** The result does not depend on whether the **arguments overlap**, so we can for instance concatenate a slice with itself:

    a := []int{1, 2}
    a = append(a, a...) // a == [1 2 1 2]

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
