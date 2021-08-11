<span class="underline"></span>

<span class="underline"></span>

## Further reading

[iota](iota.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

<span class="underline"></span>

## Top Algorithm Articles

1.  [Dynamic programming vs memoization vs tabulation](../dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](../big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](../sliding-window-example.html)
4.  [What makes a good loop invariant?](../what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](../random-point-within-circle.html)

[**See all articles**](../index.html)

# Go: Enumeration (enum) with string representation

A group of constants enumerated with `iota` might do the job:

    const (
            Sunday    int = iota // Sunday == 0
            Monday               // Monday == 1
            Tuesday              // Tuesday == 2
            Wednesday            // …
            Thursday
            Friday
            Saturday
    )

`iota` represents successive integer constants 0, 1, 2,…; it resets to 0 whenever the word `const` appears in the source code and increments after each const specification.

Above, we also rely on the fact that expressions are implicitly repeated in a parenthesized const declaration—this indicates a repetition of the preceding expression and its type.

You could also introduce a new type…

    type Suite int

    const (
            Spades Suite = iota
            Hearts
            Diamonds
            Clubs
    )

…and give it a `String` function:

    func (s Suite) String() string {
            return [...]string{"Spades", "Hearts", "Diamonds", "Clubs"}[s]
    }

Here is the new type in action:

    var s Suite = Hearts
    fmt.Print(s)
    switch s {
    case Spades:
            fmt.Println(" are best.")
    case Hearts:
            fmt.Println(" are second best.")
    default:
            fmt.Println(" aren't very good.")
    }

    Hearts are second best.

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
