<span class="underline"></span>

<span class="underline"></span>

## Further Reading

[Methods explained](methods-explained.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Constructors](constructor-best-practice.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Inheritance and object-oriented programming](inheritance-object-oriented.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

## Top Go Articles

1.  [Go gotcha](go-gotcha.html)
2.  [String handling cheat sheet](string-functions-reference-cheat-sheet.html)
3.  [Maps explained](maps-explained.html)
4.  [For loops explained](for-loop.html)
5.  [Concurrent programming](go-concurrency-tutorial.html)

[**See all 197 Go articles**](index.html)

<span class="underline"></span>

## Top Algorithm Articles

1.  [Dynamic programming vs memoization vs tabulation](../dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](../big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](../sliding-window-example.html)
4.  [What makes a good loop invariant?](../what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](../random-point-within-circle.html)

[**See all articles**](../index.html)

# Go: Public vs. private

All identifiers defined within a package are visible throughout that package.

When importing a package you can access only its **exported** identifiers.

An identifier is exported if it begins with a capital letter.

## Example

In this package, the only exported identifiers are `StopWatch` and `Start`:

    package timer

    import "time"

    // A StopWatch is a simple clock utility.
    // Its zero value is an idle clock with 0 total time.
    type StopWatch struct {
            start   time.Time
            total   time.Duration
            running bool
    }

    // Start turns the clock on.
    func (s *StopWatch) Start() {
            if !s.running {
                    s.start = time.Now()
                    s.running = true
            }
    }

The `StopWatch` and its exported methods can be imported and used in a different package:

    package main

    import "timer"

    func main() {
            clock := new(timer.StopWatch)
            clock.Start()
            if clock.running { // illegal
                    …
            }
    }

    ../main.go:8:15: clock.running undefined (cannot refer to unexported field or method clock.running)

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
