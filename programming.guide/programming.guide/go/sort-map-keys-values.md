## Further Reading

[Maps explained](maps-explained.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[How to sort in Go](how-to-sort-in-go.html)  
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

# Go: Sort a map by key or value

- A map is an **unordered** collection of key-value pairs.
- If you need a stable iteration order, you must maintain a separate data structure.

This example uses a sorted slice of keys to print a `map[string]int` in key order:

    m := map[string]int{"Alice": 23, "Eve": 2, "Bob": 25}

    keys := make([]string, 0, len(m))
    for k := range m {
            keys = append(keys, k)
    }
    sort.Strings(keys)

    for _, k := range keys {
            fmt.Println(k, m[k])
    }

Output:

    Alice 23
    Bob 25
    Eve 2

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
