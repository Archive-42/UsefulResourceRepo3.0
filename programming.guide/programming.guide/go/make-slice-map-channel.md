## Related / Further Reading

[Slices explained](slices-explained.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Maps explained](maps-explained.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Channels explained](channels-explained.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Default value of struct, string, slice, map](default-zero-value.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Composite literals](https://golang.org/ref/spec#Composite_literals)  
<span style="color: grey; font-style: italic; font-size: smaller">The Go Programming Language Specification</span>

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

# Go: Make slices, maps and channels

Slices, maps and channels can be created with the built-in `make` function. The memory is initialized with [zero values](default-zero-value.html).

<table><thead><tr class="header"><th>Call</th><th>Type</th><th>Description</th></tr></thead><tbody><tr class="odd"><td><code>make(T, n)</code></td><td>slice</td><td>slice of type T with length n</td></tr><tr class="even"><td><code>make(T, n, c)</code></td><td></td><td>capacity c</td></tr><tr class="odd"><td><code>make(T)</code></td><td>map</td><td>map of type T</td></tr><tr class="even"><td><code>make(T, n)</code></td><td></td><td>initial room for approximately n elements</td></tr><tr class="odd"><td><code>make(T)</code></td><td>channel</td><td>unbuffered channel of type T</td></tr><tr class="even"><td><code>make(T, n)</code></td><td></td><td>buffered channel with buffer size n</td></tr></tbody></table>

    s := make([]int, 10, 100)      // slice with len(s) == 10, cap(s) == 100
    m := make(map[string]int, 100) // map with initial room for ~100 elements
    c := make(chan int, 10)        // channel with a buffer size of 10

Slices, arrays and maps can also be created with [composite literals](https://golang.org/ref/spec#Composite_literals):

    s := []string{"f", "o", "o"} // slice with len(s) == 3, cap(s) == 3
    a := [...]int{1, 2}          // array with len(a) == 2
    m := map[string]float64{     // map with two key-value elements
            "e":  2.71828,
            "pi": 3.1416,
    }

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
