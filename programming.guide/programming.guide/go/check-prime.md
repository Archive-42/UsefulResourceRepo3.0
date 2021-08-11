



## Further Reading

[Package big](https://golang.org/pkg/math/big/)  
<span style="color: grey; font-style: italic; font-size: smaller">The Go Programming Language</span>

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

# Go: Check if a number is prime

## Ints

For integer types, use [`ProbablyPrime(0)`](https://golang.org/pkg/math/big/#Int.ProbablyPrime) from package [`math/big`](https://golang.org/pkg/math/big/). (This primality test is 100% accurate for inputs less than 2<sup>64</sup>.)

    const i = 1212121
    if big.NewInt(i).ProbablyPrime(0) {
            fmt.Println(i, "is prime")
    } else {
            fmt.Println(i, "is not prime")
    }

    1212121 is prime

## Larger numbers

For larger numbers, you need to provide the desired number of tests `n` to [`ProbablyPrime(n)`](https://golang.org/pkg/math/big/#Int.ProbablyPrime). For *n* tests, the probability of returning true for a randomly chosen non-prime is at most (1/4)<sup>_n_</sup>. A common choice is to use *n* = 20; it gives the false positive rate 0.000,000,000,001.

    z := new(big.Int)
    fmt.Sscan("170141183460469231731687303715884105727", z)
    if z.ProbablyPrime(20) {
            fmt.Println(z, "is probably prime")
    } else {
            fmt.Println(z, "is not prime")
    }

    170141183460469231731687303715884105727 is probably prime

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
