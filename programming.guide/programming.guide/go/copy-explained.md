



## Related

[Slices explained](slices-explained.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Append function explained](append-explained.html)  
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

# Go: Copy function explained

The built-in [`copy`](https://golang.org/ref/spec#Appending_and_copying_slices) function copies elements into a destination slice `dst` from a source slice `src`:

    func copy(dst, src []Type) int

It returns the number of elements copied, which will be the minimum of `len(dst)` and `len(src)`.

The result does not depend on whether the arguments overlap.

## Special case

It is legal to copy bytes from a string to a slice of bytes:

    copy(dst []byte, src string) int

## Examples

**Example:** Copy from one slice to another:

    var s = make([]int, 3)
    n := copy(s, []int{0, 1, 2, 3}) // n == 3, s == []int{0, 1, 2}

**Example:** Copy from a slice to itself:

    s := []int{0, 1, 2}
    n := copy(s, s[1:]) // n == 2, s == []int{1, 2, 2}

**Example:** Copy from a string to a byte slice:

    var b = make([]byte, 5)
    copy(b, "Hello, world!") // b == []byte("Hello")

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
