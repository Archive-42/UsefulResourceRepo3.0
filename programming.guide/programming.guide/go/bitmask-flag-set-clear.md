



## Further reading

[Bitwise operators cheat sheet](bitwise-operator-cheat-sheet.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[iota](iota.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Enumeration (enum) with string representation](define-enumeration-string.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Your basic int: a tribute to an underrated data type](https://github.com/yourbasic/int)  
<span style="color: grey; font-style: italic; font-size: smaller">github.com/yourbasic</span>

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

# Go: Bitmasks and flags

A bitmask is a small set of booleans, often called flags, represented by the bits in a single number.

    type Bits uint8

    const (
            F0 Bits = 1 << iota
            F1
            F2
    )

    func Set(b, flag Bits) Bits    { return b | flag }
    func Clear(b, flag Bits) Bits  { return b &^ flag }
    func Toggle(b, flag Bits) Bits { return b ^ flag }
    func Has(b, flag Bits) bool    { return b&flag != 0 }

    func main() {
            var b Bits
            b = Set(b, F0)
            b = Toggle(b, F2)
            for i, flag := range []Bits{F0, F1, F2} {
                    fmt.Println(i, Has(b, flag))
            }
    }

    0 true
    1 false
    2 true

## Larger bit sets

To represent larger sets of bits, you may want to use a custom data structure. The repository [`github.com/yourbasic/bit`](https://github.com/yourbasic/bit) provides an implementation that uses a bit array consisting of 64-bit words.

Because a bit array uses bit-level parallelism, limits memory access, and efficiently uses the data cache, it often outperforms other data structures. Here is an example that shows how to create the set of all primes less than _n_ in _O_(*n* log log *n*) time using the [`bit.Set`](https://godoc.org/github.com/yourbasic/bit#Set) data structure from the [`github.com/yourbasic/bit`](https://github.com/yourbasic/bit) package. Try the code with _n_ equal to a few hundred millions and be pleasantly surprised.

    // Sieve of Eratosthenes
    const n = 50
    sieve := bit.New().AddRange(2, n)
    sqrtN := int(math.Sqrt(n))
    for p := 2; p <= sqrtN; p = sieve.Next(p) {
        for k := p * p; k < n; k += p {
            sieve.Delete(k)
        }
    }
    fmt.Println(sieve)

    {2 3 5 7 11 13 17 19 23 29 31 37 41 43 47}

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
