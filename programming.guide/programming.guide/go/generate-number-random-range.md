



## Further Reading

[Random Generators: What is a seed?](../random-generators-what-is-a-seed.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Cryptographically secure random numbers](crypto-rand-int.html)  
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

# Go: Generate a random number in a given range

Use the [`rand.Seed`](https://golang.org/pkg/math/rand/#Seed) and [`rand.Intn`](https://golang.org/pkg/math/rand/#Intn) functions in package [`math/rand`](https://golang.org/pkg/math/rand/) to generate a random number between `a` and `b`:

    rand.Seed(time.Now().UnixNano())
    n := a + rand.Intn(b-a+1)

Without the call to `rand.Seed`, a program will produce the same sequence of pseudo-random numbers for each execution.

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
