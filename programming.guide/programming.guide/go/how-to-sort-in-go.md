<span class="underline"></span>

<span class="underline"></span>

## Related

[Time complexity explained](../time-complexity-explained.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Big O notation explained](../big-o-notation-explained.html)  
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

# Go: How to sort in Go

All algorithms in the Go sort package make _O_(*n* log *n*) comparisons in the worst case, where _n_ is the number of elements to be sorted.

## Sort a slice of ints, float64s or strings

Use one of the functions

- [`sort.Ints`](https://golang.org/pkg/sort/#Ints)
- [`sort.Float64s`](https://golang.org/pkg/sort/#Float64s)
- [`sort.Strings`](https://golang.org/pkg/sort/#Strings)

<!-- -->

    s := []int{4, 2, 3, 1}
    sort.Ints(s)
    fmt.Println(s) // [1 2 3 4]

## Sort with custom compare function

- Use the function [`sort.Slice`](https://golang.org/pkg/sort/#Slice). It sorts a slice using a provided `less(i, j int) bool` function.
- To sort the slice while keeping the original order of equal elements, use [`sort.SliceStable`](https://golang.org/pkg/sort/#SliceStable) instead.

<!-- -->

    family := []struct {
            Name string
            Age  int
    }{
            {"Alice", 23},
            {"David", 2},
            {"Eve", 2},
            {"Bob", 25},
    }

    // Sort by age, keeping original order or equal elements.
    sort.SliceStable(family, func(i, j int) bool {
            return family[i].Age < family[j].Age
    })
    fmt.Println(family) // [{David 2} {Eve 2} {Alice 23} {Bob 25}]

## Sort custom data structures

- Use the generic [`sort.Sort`](https://golang.org/pkg/sort/#Sort) and [`sort.Stable`](https://golang.org/pkg/sort/#Stable) functions.
- They sort any collection that implements [`sort.Interface`](https://golang.org/pkg/sort/#Interface).

<!-- -->

    type Interface interface {
            // Len is the number of elements in the collection.
            Len() int
            // Less reports whether the element with
            // index i should sort before the element with index j.
            Less(i, j int) bool
            // Swap swaps the elements with indexes i and j.
            Swap(i, j int)
    }

Here is an example:

    type Person struct {
            Name string
            Age  int
    }

    // ByAge implements sort.Interface based on the Age field.
    type ByAge []Person

    func (a ByAge) Len() int           { return len(a) }
    func (a ByAge) Less(i, j int) bool { return a[i].Age < a[j].Age }
    func (a ByAge) Swap(i, j int)      { a[i], a[j] = a[j], a[i] }

    func main() {
            family := []Person{
                    {"Alice", 23},
                    {"Eve", 2},
                    {"Bob", 25},
            }
            sort.Sort(ByAge(family))
            fmt.Println(family) // [{Eve 2} {Alice 23} {Bob 25}]
    }

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
