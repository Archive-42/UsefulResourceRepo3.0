<span class="underline"></span>

<span class="underline"></span>

Related
-------

[Time complexity explained](../time-complexity-explained.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Big O notation explained](../big-o-notation-explained.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[How to sort in Go](how-to-sort-in-go.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

Top Go Articles
---------------

1.  [Go gotcha](go-gotcha.html)
2.  [String handling cheat sheet](string-functions-reference-cheat-sheet.html)
3.  [Maps explained](maps-explained.html)
4.  [For loops explained](for-loop.html)
5.  [Concurrent programming](go-concurrency-tutorial.html)

[**See all 197 Go articles**](index.html)

<span class="underline"></span>

Top Algorithm Articles
----------------------

1.  [Dynamic programming vs memoization vs tabulation](../dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](../big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](../sliding-window-example.html)
4.  [What makes a good loop invariant?](../what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](../random-point-within-circle.html)

[**See all articles**](../index.html)

Go: Binary search
=================

Use one of the **binary search** functions: [`sort.SearchInts`](https://golang.org/pkg/sort/#SearchInts), [`sort.SearchFloat64s`](https://golang.org/pkg/sort/#SearchFloat64s) or [`sort.SearchStrings`](https://golang.org/pkg/sort/#SearchStrings).

They all have the signature:

    func SearchType(a []Type, x Type) int

and return

-   the smallest index `i` at which `x <= a[i]`; or
-   `len(a)` if there is no such index.

The slice must be sorted in **ascending order**.

    a := []string{"A", "C", "C"}

    fmt.Println(sort.SearchStrings(a, "A")) // 0
    fmt.Println(sort.SearchStrings(a, "B")) // 1
    fmt.Println(sort.SearchStrings(a, "C")) // 1
    fmt.Println(sort.SearchStrings(a, "D")) // 3

Generic binary search
---------------------

Use the **generic binary search** function [`sort.Search`](https://golang.org/pkg/sort/#Search):

    func Search(n int, f func(int) bool) int

It returns

-   the smallest index `i` at which `f(i)` is true; or
-   `n` if there is no such index.

It requires that `f` is false for some (possibly empty) prefix of the input range and then true for the remainder.

This example mirrors the one above, but uses the generic [`sort.Search`](https://golang.org/pkg/sort/#Search) instead of [`sort.SearchInts`](https://golang.org/pkg/sort/#SearchInts).

    a := []string{"A", "C", "C"}
    x := "C"

    i := sort.Search(len(a), func(i int) bool { return x <= a[i] })
    if i < len(a) && a[i] == x {
            fmt.Printf("Found %s at index %d in %v.\n", x, i, a)
    } else {
            fmt.Printf("Did not find %s in %v.\n", x, a)
    }
    // Output: Found C at index 1 in [A C C].

Complexity
----------

Binary search runs in worst-case logarithmic time, making *O*(log *n*) comparisons, where *n* is the size of the array.

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
