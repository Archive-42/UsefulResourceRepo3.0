<span class="underline"></span>

<span class="underline"></span>

## Related

[Slices explained](slices-explained.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Implement a stack (LIFO)](implement-stack.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

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

# Go: Implement a FIFO queue

A simple way to implement a temporary queue in Go is to use a slice: - to enqueue you use the built-in `append` function, and - to dequeue you slice off the first element.

    // Create
    var queue []string

    // Enqueue
    queue = append(queue, "Hello ")
    queue = append(queue, "world!")

    for len(queue) > 0 {
            // Print first
            fmt.Print(queue[0])

            // Dequeue
            queue = queue[1:]
    }
    // Output: Hello world!

## Watch out for memory leaks

You may want to remove the first element before dequeuing:

    // Dequeue
    queue[0] = "" // to avoid memory leak
    queue = queue[1:]

Also, note that the memory allocated for the array is never returned. For a long-living queue you should probably use a dynamic data structure, such as a linked list.

## Linked list

The [`container/list`](https://golang.org/pkg/container/list/) package implements a doubly linked list which can be used as a queue.

    // Create
    queue := list.New()

    // Enqueue
    queue.PushBack("Hello ")
    queue.PushBack("world!")

    for queue.Len() > 0 {
            // Print first
            e := queue.Front()
            fmt.Print(e.Value)

            // Dequeue
            queue.Remove(e)
    }
    // Output: Hello world!

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
