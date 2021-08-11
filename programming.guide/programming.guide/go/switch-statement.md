



## Further Reading

[Switch statements](https://golang.org/ref/spec#Switch_statements)  
<span style="color: grey; font-style: italic; font-size: smaller">The Go Programming Language Specification</span>

[For loops explained](for-loop.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Select explained](select-explained.html)  
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

# Go: Switch statement

A switch statement is a shorter way to write a sequence of if-else statements.

## Basics

    switch time.Now().Weekday() {
    case time.Saturday:
            fmt.Println("Today is Saturday.")
    case time.Sunday:
            fmt.Println("Today is Sunday.")
    default:
            fmt.Println("Today is a weekday.")
    }

- A switch statement runs the first case equal to the condition expression.
- The cases are evaluated from top to bottom, stopping when a case succeeds.

Unlike C and Java, the case expressions do not need to be constants. They can be arbitrary expressions as will be seen in the section below.

## No condition

    hour := time.Now().Hour()
    switch { // Same as: switch true
    case hour < 12:
            fmt.Println("Good morning!")
    case hour < 17:
            fmt.Println("Good afternoon!")
    default:
            fmt.Println("Good evening!")
    }

## Case lists

    func whiteSpace(c rune) bool {
        switch c {
        case ' ', '\t', '\n', '\f', '\r':
            return true
        }
        return false
    }

## Fall through

    switch 2 {
    case 1:
            fmt.Println("1")
            fallthrough
    case 2:
            fmt.Println("2")
            fallthrough
    case 3:
            fmt.Println("3")
    }

    2
    3

- A `fallthrough` statement transfers control to the next case.
- It may be used only as the final statement in a clause.

## Exit a switch

A `break` statement terminates execution of the innermost `for`, `switch`, or `select` statement.

## Execution order

    func Foo(n int) int {
            fmt.Println(n)
            return n
    }

    func main() {
            switch Foo(1) {
            case Foo(0), Foo(1), Foo(2):
                    fmt.Println("First case")
                    fallthrough
            case Foo(3):
                    fmt.Println("Second case")
            }
    }

    1
    0
    1
    First case
    Second case

- First the switch expression is evaluated once.
- Then case expressions are evaluated left-to-right and top-to-bottom;
- the first one that equals the switch expression triggers execution of the statements of the associated case; the other cases are skipped.

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
