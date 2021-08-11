



## Further reading

[Print with fmt cheat sheet](fmt-printf-reference-cheat-sheet.html)  
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

# Go: Build and concatenate strings efficiently

## Most of the time

For simple cases where performance is a non-issue, [`fmt.Sprintf`](https://golang.org/pkg/fmt/#Sprintf) is your friend:

    s := fmt.Sprintf("Size: %d MB.", 85) // s == "Size: 85 MB."

The [Print with fmt cheat sheet](fmt-printf-reference-cheat-sheet.html) lists the most common formatting verbs and flags.

## String builder (Go 1.10)

The [`strings.Builder`](https://tip.golang.org/pkg/strings/#Builder) type, which will be introduced in [**Go 1.10**](https://tip.golang.org/doc/go1.10), is used to efficiently build a string using write methods.

- It offers a subset of the [`bytes.Buffer`](https://golang.org/pkg/bytes/#Buffer) methods that allows it to safely avoid redundant copying.
- The [`Grow`](https://tip.golang.org/pkg/strings/#Builder.Grow) method can be used to preallocate memory when the maximum size of the string is known.

<!-- -->

    var b strings.Builder
    b.Grow(16)
    b.WriteString("Size: ")
    fmt.Fprintf(&b, "%d", 85)
    b.WriteString(" MB.")
    s := b.String() // No copying!

## Before Go 1.10

Use [`fmt.Fprintf`](https://golang.org/pkg/fmt/#Fprintf) to print into a [`bytes.Buffer`](https://golang.org/pkg/bytes/#Buffer):

    var buf bytes.Buffer
    for i, p := range []int{2, 3, 5, 7, 11, 13} {
            fmt.Fprintf(&buf, "%d:%d, ", i+1, p)
    }
    buf.Truncate(buf.Len() - 2) // Remove trailing ", "
    s := buf.String()           // s == "1:2, 2:3, 3:5, 4:7, 5:11, 6:13"

This solution is pretty efficient but may generate some excess garbage. For higher performance, you can try to use the append functions in package [`strconv`](https://golang.org/pkg/strconv/):

    buf := []byte("Size: ")
    buf = strconv.AppendInt(buf, 85, 10)
    buf = append(buf, " MB."...)
    s := string(buf)

If the expected maximum length of the string is known, you may want to preallocate the slice:

    buf := make([]byte, 0, 16)
    buf = append(buf, "Size: "...)
    buf = strconv.AppendInt(buf, 85, 10)
    buf = append(buf, " MB."...)
    s := string(buf)

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
