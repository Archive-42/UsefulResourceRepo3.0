## Further Reading

[Constructors](constructor-best-practice.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Methods explained](methods-explained.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Interfaces explained](interfaces-explained.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Public vs. private](public-private.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Embedding](https://golang.org/doc/effective_go.html#embedding)  
<span style="color: grey; font-style: italic; font-size: smaller">Effective Go</span>

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

# Go: Inheritance and object-oriented programming

Inheritance in traditional object-oriented programming offers three features in one. When a `Dog` inherits from an `Animal`:

1.  the `Dog` class reuses code from the `Animal` class,
2.  a variable `x` of type `Animal` can refer to either a `Dog` or an `Animal`,
3.  `x.Eat()` will choose an `Eat` method based on what type of object `x` refers to.

In object-oriented lingo, these features are known as **code reuse**, **poly­mor­phism** and **dynamic dispatch**.

All of these are available in Go, using separate constructs:

- **composition** and **embedding** provide code reuse,
- **interfaces** take care of polymorphism and dynamic dispatch.

## Code reuse: composition

Don't worry about type hierarchies when starting a new Go project; it's easy to introduce polymorphism and dynamic dispatch later on.

If a `Dog` needs some or all of the functionality of an `Animal`, simply use **composition**:

    type Animal struct {
            // …
    }

    type Dog struct {
            beast Animal
            // …
    }

This gives you full freedom to use the `Animal` part of your `Dog` as needed. Yes, it's that simple.

## Code reuse: embedding

If the `Dog` class inherits **the exact behavior** of an `Animal`, this approach can result in some tedious coding:

    type Animal struct {
            // …
    }

    func (a *Animal) Eat()   { … }
    func (a *Animal) Sleep() { … }
    func (a *Animal) Breed() { … }

    type Dog struct {
            beast Animal
            // …
    }

    func (a *Dog) Eat()   { a.beast.Eat() }
    func (a *Dog) Sleep() { a.beast.Sleep() }
    func (a *Dog) Breed() { a.beast.Breed() }

This code pattern is known as **delegation**.

Go uses **embedding** for situations like this. The declaration of the `Dog` struct and it's three methods can be reduced to:

    type Dog struct {
            Animal
            // …
    }

## Polymorphism and dynamic dispatch: interfaces

Keep your interfaces short, and introduce them only when needed.

Further down the road your project might have grown to include more animals. At this point you can introduce polymorphism and dynamic dispatch using **interfaces**.

If you need to put all your pets to sleep, you can define a `Sleeper` interface:

    type Sleeper interface {
            Sleep()
    }

    func main() {
            pets := []Sleeper{new(Cat), new(Dog)}
            for _, x := range pets {
                    x.Sleep()
            }
    }

No explicit declaration is required by the `Cat` and `Dog` types. Any type that provides the methods named in an inter­face may be treated as an imple­mentation.

> When I see a bird that walks like a duck and swims like a duck and quacks like a duck, I call that bird a duck.<span class="quote-source">James Whitcomb Riley</span>

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
