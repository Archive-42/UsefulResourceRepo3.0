<span class="underline"></span>

<span class="underline"></span>

Top Go Articles
---------------

1.  [Go gotcha](go-gotcha.html)
2.  [String handling cheat sheet](string-functions-reference-cheat-sheet.html)
3.  [Maps explained](maps-explained.html)
4.  [For loops explained](for-loop.html)
5.  [Concurrent programming](go-concurrency-tutorial.html)

[**See all 197 Go articles**](index.html)

<span class="underline"></span>

Top Algorithm Articles
----------------------

1.  [Dynamic programming vs memoization vs tabulation](../dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](../big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](../sliding-window-example.html)
4.  [What makes a good loop invariant?](../what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](../random-point-within-circle.html)

[**See all articles**](../index.html)

Go: Compare slices (arrays)
===========================

In general, the preferred approach is to write your own code for comparing slices.

    // Equal tells whether a and b contain the same elements.
    // A nil argument is equivalent to an empty slice.
    func Equal(a, b []int) bool {
            if len(a) != len(b) {
                    return false
            }
            for i, v := range a {
                    if v != b[i] {
                            return false
                    }
            }
            return true
    }

Byte slices
-----------

For comparing bytes slices, use the optimized [`bytes.Equal`](https://golang.org/pkg/bytes/#Equal). This function also treats nil arguments as equivalent to empty slices.

reflect.DeepEqual
-----------------

For testing purposes, you may want to use [`reflect.DeepEqual`](https://golang.org/pkg/reflect/#DeepEqual).

    var a []int = nil
    var b []int = make([]int, 0)
    fmt.Println(reflect.DeepEqual(a, b)) // false

The performance of this function is much worse than for the code above, but it's useful in test cases where simplicity and correctness are crucial. However, the semantics are quite complicated:

> `func DeepEqual(x, y interface{}) bool`
>
> `DeepEqual` reports whether `x` and `y` are "deeply equal," defined as follows. Two values of identical type are deeply equal if one of the following cases applies. Values of distinct types are never deeply equal.
>
> **Array values** are deeply equal when their corresponding elements are deeply equal.
>
> **Struct values** are deeply equal if their corresponding fields, both exported and unexported, are deeply equal.
>
> **Func values** are deeply equal if both are nil; otherwise they are not deeply equal.
>
> **Interface values** are deeply equal if they hold deeply equal concrete values.
>
> **Map values** are deeply equal when all of the following are true: they are both nil or both non-nil, they have the same length, and either they are the same map object or their corresponding keys (matched using Go equality) map to deeply equal values.
>
> **Pointer values** are deeply equal if they are equal using Go's `==` operator or if they point to deeply equal values.
>
> **Slice values** are deeply equal when all of the following are true: they are both nil or both non-nil, they have the same length, and either they point to the same initial entry of the same underlying array (that is, `&x[0] == &y[0]`) or their corresponding elements (up to length) are deeply equal. Note that a non-nil empty slice and a nil slice (for example, `[]byte{}` and `[]byte(nil)`) are not deeply equal.
>
> **Other values** - numbers, bools, strings, and channels - are deeply equal if they are equal using Go's `==` operator.
>
> In general `DeepEqual` is a recursive relaxation of Go's `==` operator. However, this idea is impossible to implement without some inconsistency. Specifically, it is possible for a value to be unequal to itself, either because it is of func type (uncomparable in general) or because it is a floating-point NaN value (not equal to itself in floating-point comparison), or because it is an array, struct, or interface containing such a value. On the other hand, pointer values are always equal to themselves, even if they point at or contain such problematic values, because they compare equal using Go's `==` operator, and that is a sufficient condition to be deeply equal, regardless of content. `DeepEqual` has been defined so that the same short-cut applies to slices and maps: if `x` and `y` are the same slice or the same map, they are deeply equal regardless of content. <a href="https://golang.org/pkg/reflect/#DeepEqual" class="quote-source">Package reflect: DeepEqual</a>

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
