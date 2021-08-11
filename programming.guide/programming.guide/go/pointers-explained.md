## Further Reading

[Pointer vs. value receiver](pointer-vs-value-receiver.html)  
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

# Go: Pointers explained

A pointer is a vari­able that con­tains the address of an object.

- [Basics](pointers-explained.html#basics)
- [Address operator](pointers-explained.html#address-operator)
- [Pointer indirection](pointers-explained.html#pointer-indirection)
- [Pointers as parameters](pointers-explained.html#pointers-as-parameters)

## Basics

Structs and arrays are **copied** when used in assignments and passed as arguments to functions. With pointers this can be **avoided**.

Pointers store **addresses** of objects, which can be passed around efficiently, rather than actual objects:

- use `*T` as type for a pointer,
- and `new` to allocate and get the address of an object.

<!-- -->

    type Person struct {
            Name string
    }

    var pp *Person = new(Person) // pp holds the address of the new struct

The variable declaration can be written more compactly:

    pp := new(Person)

## Address operator

To get the address of an object, use the `&amp;` operator like this:

    p := Person{"Alice"} // p holds the actual struct
    pp := &p             // pp holds the address of the struct

The `&amp;` operator can also be used with **composite literals**. The above two lines can be written as:

    pp := &Person{"Alice"}

## Pointer indirection

For a pointer `x`, the **pointer indirection** `*x` denotes the value which `x` points to. Pointer indirection is rarely used, since Go can automatically take the address of a variable:

    pp := new(Person)
    pp.Name = "Alice" // same as (*pp).Name = "Alice"

## Pointers as parameters

When using a pointer to modify an object, you're affecting everybody that uses that object.

    // Bob is a function that has no effect.
    func Bob(p Person) {
            p.Name = "Bob" // changes only the local copy
    }

    // Charlie sets pp.Name to "Charlie".
    func Charlie(pp *Person) {
            pp.Name = "Charlie"
    }

    func main() {
            p := Person{"Alice"}

            Bob(p)
            fmt.Println(p) // prints {Alice}

            Charlie(&p)
            fmt.Println(p) // prints {Charlie}
    }

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
