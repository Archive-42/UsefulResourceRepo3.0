## Further reading

[Enumeration (enum) with string representation](define-enumeration-string.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Iota](https://golang.org/ref/spec#Iota)  
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

# Go: iota

Iota is a basic tool for enumerated constants.

- [Basics](iota.html#basics)
- [Start at 1](iota.html#start-at-1)
- [Skip value](iota.html#skip-value)
- [Enumeration](iota.html#enumeration)

## Basics

The predeclared `iota` identifier resets to 0 whenever the word `const` appears in the source code and increments after each const specification:

    const (
            C0 = iota
            C1 = iota
            C2 = iota
    )
    fmt.Println(C0, C1, C2) // "0 1 2"

This can be simplified to

    const (
            C0 = iota
            C1
            C2
    )

In a parenthesized const declaration expressions can be implicitly repeated—this indicates a repetition of the preceding expression.

## Start at 1

    const (
            C1 = iota + 1
            C2
            C3
    )
    fmt.Println(C1, C2, C3) // "1 2 3"

## Skip value

    const (
            C1 = iota + 1
            _
            C3
            C4
    )
    fmt.Println(C1, C3, C4) // "1 3 4"

## Enumeration

    type Suite int

    const (
            Spades Suite = iota
            Hearts
            Diamonds
            Clubs
    )

    func (s Suite) String() string {
            return [...]string{"Spades", "Hearts", "Diamonds", "Clubs"}[s]
    }

See [Define an enumeration (enum) with a string representation](define-enumeration-string.html) for more details on how to create and use enumerations in Go.

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
