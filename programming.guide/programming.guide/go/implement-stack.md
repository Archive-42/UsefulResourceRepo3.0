## Related

[Slices explained](slices-explained.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Implement a FIFO queue](implement-fifo-queue.html)  
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

# Go: Implement a stack (LIFO)

The idiomatic way to implement a stack in Go is to use a slice:

- to push you use the built-in `append` function, and
- to pop you slice off the top element.

<!-- -->

    // Create
    var stack []string

    // Push
    stack = append(stack, "world!")
    stack = append(stack, "Hello ")

    for len(stack) > 0 {
            // Print top
            n := len(stack) - 1
            fmt.Print(stack[n])

            // Pop
            stack = stack[:n]
    }
    // Output: Hello world!

## Watch out for memory leaks

If the stack is permanent and the elements temporary, you may want to remove the top element before popping the stack.

    …
    // Pop
    stack[n] = "" // to avoid memory leak
    stack = stack[:n]
    …

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
