## Further Reading

[Random Generators: What is a seed?](../random-generators-what-is-a-seed.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Fisher–Yates shuffle](https://en.wikipedia.org/wiki/Fisher%E2%80%93Yates_shuffle)  
<span style="color: grey; font-style: italic; font-size: smaller">Wikipedia</span>

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

# Go: Shuffle slice or array

The [`rand.Shuffle`](https://tip.golang.org/pkg/math/rand/#Shuffle) function, which will be introduced in [**Go 1.10**](https://tip.golang.org/doc/go1.10), shuffles an input sequence.

    a := []int{1, 2, 3, 4, 5, 6, 7, 8}
    rand.Seed(time.Now().UnixNano())
    rand.Shuffle(len(a), func(i, j int) { a[i], a[j] = a[j], a[i] })

    [5 8 6 4 3 7 2 1]

Without the call to `rand.Seed`, a program will produce the same sequence of pseudo-random numbers for each execution.

## Before Go 1.10

Use the [`rand.Seed`](https://golang.org/pkg/math/rand/#Seed) and [`rand.Intn`](https://golang.org/pkg/math/rand/#Intn) functions in package [`math/rand`](https://golang.org/pkg/math/rand/):

    a := []int{1, 2, 3, 4, 5, 6, 7, 8}
    rand.Seed(time.Now().UnixNano())
    for i := len(a) - 1; i > 0; i-- { // Fisher–Yates shuffle
            j := rand.Intn(i + 1)
            a[i], a[j] = a[j], a[i]
    }

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
