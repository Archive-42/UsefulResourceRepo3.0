## Further Reading

[Default value of struct, string, slice, map](default-zero-value.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Pointers explained](pointers-explained.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Methods explained](methods-explained.html)  
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

# Go: Structs explained

A **struct** is a typed collection of fields. It's useful for grouping data to form records.

## Defining a struct

    type Person struct {
        name string
        age  int
    }

## Using a struct

    var x Person      // x is initialized to the zero value: Person{"", 0}
        x.name = "Alice"

        var px *Person    // px is initialized to nil
        px = new(Person)  // px points to the new struct Person{"", 0}
        px.name = "Bob"

        y := Person{       // y is initialized to Person{"Alice", 0}.
            name: "Alice",
        }

        py := &Person{     // py points to the new struct Person{"Bob", 8}.
            name: "Bob",
            age:  8,
        }

        z := Person{"Cecilia", 5} // One element for each field, in given order.

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
