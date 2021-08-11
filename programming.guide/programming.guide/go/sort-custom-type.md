



## Further reading

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

# Go: How to sort a custom type in Go

- Use the function [`sort.Slice`](https://golang.org/pkg/sort/#Slice). It sorts a slice using a provided `less(i, j int) bool` function.
- To sort the slice while keeping the original order of equal elements, use [`sort.SliceStable`](https://golang.org/pkg/sort/#SliceStable) instead.

<!-- -->

    family := []struct {
            Name string
            Age  int
    }{
            {"Alice", 23},
            {"David", 2},
            {"Eve", 2},
            {"Bob", 25},
    }

    // Sort by age, keeping original order or equal elements.
    sort.SliceStable(family, func(i, j int) bool {
            return family[i].Age < family[j].Age
    })
    fmt.Println(family) // [{David 2} {Eve 2} {Alice 23} {Bob 25}]

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
