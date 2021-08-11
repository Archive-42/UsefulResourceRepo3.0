<span class="underline"></span>

<span class="underline"></span>

## Further Reading

[How to Write Go Code: Testing](https://golang.org/doc/code.html#Testing)  
<span style="color: grey; font-style: italic; font-size: smaller">The Go Programming Language</span>

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

# Go: Table-driven unit tests

Here is the code we want to test:

    package search

    // Find returns the smallest index i at which x <= a[i].
    // If there is no such index, it returns len(a).
    // The slice must be sorted in ascending order.
    func Find(a []int, x int) int {
            // binary search
            i, j := 0, len(a)
            for i < j {
                    m := i + (j-i)/2
                    // i ≤ m < j
                    if x > a[m] {
                            i = m + 1
                    } else {
                            j = m
                    }
            }
            return i
    }

- Put the test code in a file whose name ends with **\_test.go**.
- Write a function `TestXXX` with a single argument of type [`*testing.T`](https://golang.org/pkg/testing/#T). The test framework runs each such function.
- To indicate a failed test, call a failure function such as [`t.Errorf`](https://golang.org/pkg/testing/#T.Errorf).

<!-- -->

    package search

    import "testing"

    var tests = []struct {
            a   []int
            x   int
            exp int
    }{
            {[]int{}, 1, 0},
            {[]int{1, 2, 3, 3}, 0, 0},
            {[]int{1, 2, 3, 3}, 1, 0},
            {[]int{1, 2, 3, 3}, 2, 1},
            {[]int{1, 2, 3, 3}, 3, 3}, // Here's an error.
            {[]int{1, 2, 3, 3}, 4, 4},
    }

    func TestFind(t *testing.T) {
            for _, e := range tests {
                    res := Find(e.a, e.x)
                    if res != e.exp {
                            t.Errorf("Find(%v, %d) = %d, expected %d",
                                    e.a, e.x, res, e.exp)
                    }
            }
    }

Run the tests with [`go test`](https://golang.org/cmd/go/#hdr-Test_packages):

    $ go test
    --- FAIL: TestFind (0.00s)
            search_test.go:22: Find([1 2 3 3], 3) = 2, expected 3
    FAIL
    exit status 1
    FAIL    .../search      0.001s

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
