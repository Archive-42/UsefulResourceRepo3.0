## Further Reading

[Methods explained](methods-explained.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Type assertions and type switches](type-assertion-switch.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Find the type of an object](find-type-of-object.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Interfaces and other types](https://golang.org/doc/effective_go.html#interfaces_and_types)  
<span style="color: grey; font-style: italic; font-size: smaller">Effective Go</span>

[Interface types](https://golang.org/ref/spec#Interface_types)  
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

# Go: Interfaces explained

An **interface type** is a named set of method signatures.

- [Basics](interfaces-explained.html#basics)
- [Structural typing](interfaces-explained.html#structural-typing)
- [The empty interface](interfaces-explained.html#the-empty-interface)
- [Interface values](interfaces-explained.html#interface-values)
- [Equality](interfaces-explained.html#equality)

## Basics

You can declare an interface like this:

    type MyStringer interface {
            String() string
    }

A type **implements an interface** by implementing its methods.

In this example both `Temp` and `*Point` implement the `MyStringer` interface:

    type Temp int

    func (t Temp) String() string {
            return strconv.Itoa(int(t)) + " °C"
    }

    type Point struct {
            x, y int
    }

    func (p *Point) String() string {
            return fmt.Sprintf("(%d,%d)", p.x, p.y)
    }

Actually, `*Temp` also implements `MyStringer`, since the method set of a pointer type `*T` is the set of all methods with receiver `*T` or `T`.

A variable of interface type can hold any value that implements the interface methods. Calling a method on this value executes the method of its underlying type.

    var x MyStringer

    x = Temp(24)
    fmt.Println(x.String()) // "24 °C"

    x = &Point{1, 2}
    fmt.Println(x.String()) // "(1,2)"

## Structural typing

Any type that provides the methods named in an interface may be treated as an implementation of that interface. No explicit declaration is required.

In fact, the `Temp`, `*Temp` and `*Point` types also implement the [`fmt.Stringer`](https://golang.org/pkg/fmt/#Stringer) interface. The `String` method in this interface is used to print values passed as an operand to functions such as [`fmt.Println`](https://golang.org/pkg/fmt/#Println):

    var x MyStringer

    x = Temp(24)
    fmt.Println(x) // "24 °C"

    x = &Point{1, 2}
    fmt.Println(x) // "(1,2)"

## The empty interface

The interface type that specifies zero methods is known as the **empty interface**:

    interface{}

A variable of empty interface type can hold values of any type since every type implements at least zero methods:

    var x interface{}

    x = 2.4
    fmt.Println(x) // "2.4"

    x = &Point{1, 2}
    fmt.Println(x) // "(1,2)"

The [`fmt.Println`](https://golang.org/pkg/fmt/#Println) function is a chief example from the standard library. It takes any number of arguments of any type:

    func Println(a ...interface{}) (n int, err error)

## Interface values

A **interface value** is represented as a pair of a **concrete value** and a **dynamic type**:

    [Value, Type]

In a call to [`fmt.Printf`](https://golang.org/pkg/fmt/#Printf), you can use `%v` to print the concrete value and `%T` to print the dynamic type:

    var x MyStringer
    fmt.Printf("%v %T\n", x, x) // "<nil> <nil>"

    x = Temp(24)
    fmt.Printf("%v %T\n", x, x) // "24 °C main.Temp"

    x = &Point{1, 2}
    fmt.Printf("%v %T\n", x, x) // "(1,2) *main.Point"

    x = (*Point)(nil)
    fmt.Printf("%v %T\n", x, x) // "<nil> *main.Point"

The **zero value** of an interface type is nil, which is represented as `[nil, nil]`.

Calling a method on a nil interface is a run-time error. However, it's quite common to write methods that can handle a receiver value `[nil, T]`, where `T != nil`.

You can also use **type assertions**, **type switches** and **reflection** to access the dynamic type of an interface value. The article [Find the type of an object](find-type-of-object.html) has more details.

## Equality

Two interface values are equal if they have equal concrete values and identical dynamic types, or if both are nil.

A value `t` of interface type `T` and a value `x` of non-interface type `X` are equal if

- `t`'s concrete value is equal to `x` and
- `t`'s dynamic type is identical to `X`.

<!-- -->

    var x MyStringer
    fmt.Println(x, x == nil) // "<nil> true"

    x = (*Point)(nil)
    fmt.Println(x, x == nil) // "<nil> false"

In the second print statement, the concrete value of `x` equals `nil`, but its dynamic type is `*Point`, which is not `nil`.

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
