



## Related

[What is a rune?](rune.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Convert rune slice (array) to string](convert-rune-slice-to-string.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Iterator pattern](iterator-generator-pattern.html)  
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

# Go: Generate all permutations of a slice or string

    // Perm calls f with each permutation of a.
    func Perm(a []rune, f func([]rune)) {
            perm(a, f, 0)
    }

    // Permute the values at index i to len(a)-1.
    func perm(a []rune, f func([]rune), i int) {
            if i > len(a) {
                    f(a)
                    return
            }
            perm(a, f, i+1)
            for j := i + 1; j < len(a); j++ {
                    a[i], a[j] = a[j], a[i]
                    perm(a, f, i+1)
                    a[i], a[j] = a[j], a[i]
            }
    }

Example usage:

    Perm([]rune("abc"), func(a []rune) {
            fmt.Println(string(a))
    })

Output:

    abc
    acb
    bac
    bca
    cba
    cab

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
