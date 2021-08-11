



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

# Go: Check if a file or directory exists

Use the [`os.Stat`](https://golang.org/pkg/os/#Stat) and [`os.IsNotExist`](https://golang.org/pkg/os/#IsNotExist) functions:

    filepath := "/dev/null"
    if _, err := os.Stat(filepath); !os.IsNotExist(err) {
            fmt.Println(filepath, "exists")
            // If there was an error, it could for instance
            // be related to a permission error.
    }

**Output:**

    /dev/null exists

**Warning:** A file that is hidden from the current process (or user executing the process) will, of course, not be visible.

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
