



## Related

[Binary search](binary-search.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[How to sort in Go](how-to-sort-in-go.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Maps explained](maps-explained.html)  
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

# Go: Find an element in a slice

Go has no generic search function for slices or arrays. It's straightforward to write your own **linear search**.

    // Contains tells whether a contains x.
    func Contains(a []string, x string) bool {
            for _, n := range a {
                    if x == n {
                            return true
                    }
            }
            return false
    }

    // Find returns the smallest index i at which x == a[i],
    // or len(a) if there is no such index.
    func Find(a []string, x string) int {
            for i, n := range a {
                    if x == n {
                            return i
                    }
            }
            return len(a)
    }

## More efficient alternatives

If the slice is sorted, the search can be performed more efficiently with a [**binary search**](binary-search.html).

If you are doing many searches, consider using a [**map**](maps-explained.html) instead.

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
