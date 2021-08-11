



## Further Reading

[Function types and values](function-pointer-type-declaration.html)  
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

# Go: Function literals and closures

A **function literal**, or **lambda**, represents a function without a name.

In this code snippet a function literal is passed as the `less` argument of the [`sort.Slice`](https://golang.org/pkg/sort/#Slice) function.

    people := []string{"Alice", "Bob", "Dave"}
    sort.Slice(people, func(i, j int) bool {
            return len(people[i]) < len(people[j])
    })
    fmt.Println(people)
    // Output: [Bob Dave Alice]

It could also have been stored in an intermediate variable:

    people := []string{"Alice", "Bob", "Dave"}
    less := func(i, j int) bool {
            return len(people[i]) < len(people[j])
    }
    sort.Slice(people, less)

Note that the `less` function is a **closure**: it references the `people` variable, which is declared outside the function.

## Closures

Function literals are **closures**: they may refer to variables defined in a enclosing function. Such variables

- are shared between the surrounding function and the function literal,
- and survive as long as they are accessible.

In this example, the function literal uses the local variable `n` from the enclosing scope to count the number of times it has been invoked.

    // NewCounter returns a function Count.
    // Count prints the number of times it has been invoked.
    func NewCounter() (Count func()) {
            n := 0
            return func() {
                    n++
                    fmt.Println(n)
            }
    }

    func main() {
            counter := NewCounter()
            otherCounter := NewCounter()

            counter()      // 1
            counter()      // 2
            counter()      // 3
            otherCounter() // 1 (different n)
            otherCounter() // 2
            counter()      // 4
    }

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
