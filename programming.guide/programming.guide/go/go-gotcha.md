<span class="underline"></span>

<span class="underline"></span>

Top Go Articles
---------------

1.  Go gotcha
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

Go gotcha
=========

26 pitfalls and corner cases

*We hope this collection of common mistakes in Go will help you spot similar traps and save you time when debugging your own code.*

<a href="gotcha-assignment-entry-nil-map.html" class="button">Take quiz</a>

Table of contents
-----------------

1.  [Go gotcha: Why can't I add elements to my map?](gotcha-assignment-entry-nil-map.html)
    You can't assign an entry to a nil map in Go.

2.  [Go gotcha: What's a nil pointer dereference?](gotcha-nil-pointer-dereference.html)
    You can't follow the nil pointer.

3.  [Go gotcha: Multiple values in single value context?](gotcha-multiple-value-sinlge-value-context.html)
    If a function returns multiple values, you must use all of them.

4.  [Go gotcha: Why doesn't this function change my array?](gotcha-function-doesnt-change-array.html)
    Arrays in Go are values: when you pass an array to a function it gets a copy of the original array data.

5.  [Go gotcha: Two variables with the same name?](gotcha-shadowing-variables.html)
    An identifier declared in a block may be redeclared in an inner block.

6.  [Go gotcha: Extra comma in slice literal](gotcha-missing-comma-slice-array-map-literal.html)
    In a multi-line slice, array or map literal, every line must end with a comma.

7.  [Go gotcha: Why can't I update my string?](gotcha-strings-are-immutable.html)
    Go strings are read-only byte slices (with a few extra properties).

8.  [Go gotcha: Why aren't the characters concatenated?](gotcha-concatenate-rune-string.html)
    Characters (rune literals) are numbers in Go.

9.  [Go gotcha: What happened to ABBA?](gotcha-trim-string.html)
    The Trim functions strip all Unicode code points contained in a cutset.

10. [Go gotcha: What happened to my copy?](gotcha-copy-missing.html)
    Copy copies the minimum number of elements in the destination and source slices.

11. [Go gotcha: Why doesn't append work every time?](gotcha-append.html)
    If there is enough capacity, append reuses the underlying array.

12. [Go gotcha: Why can't I print large numbers? (constant overflows int)](gotcha-constant-overflows-int.html)
    An untyped integer constant is converted to an int when the type can't be inferred from the context.

13. [Go gotcha: Why doesn't increment (++) and decrement (--) work?](gotcha-increment-decrement-statement.html)
    In Go increment and decrement are statements written with postfix notation.

14. [Go gotcha: Why is my computation wrong?](gotcha-operator-precedence.html)
    The multiplication, division, and remainder operators have the same precedence.

15. [Go gotcha: Why does Go and Pythagoras disagree?](gotcha-bitwise-operators.html)
    The circumflex (^) denotes bitwise XOR in Go.

16. [Go gotcha: Why doesn't this loop end?](gotcha-integer-overflow-wrap-around.html)
    An integer overflow occurs when an arithmetic operation tries to create a value that is outside the range that can be represented.

17. [Go gotcha: Numbers that start with zero](gotcha-octal-decimal-hexadecimal-literal.html)
    Octal literals start with 0, hexadecimal with 0x, an decimal literals never start with zero.

18. [Go gotcha: What's wrong with the remainder (modulo) operator?](gotcha-remainder-modulo-operator.html)
    The remainder operator can give negative answers if the dividend is negative.

19. [Go gotcha: Why can't I multiply a time.Duration with an integer?](gotcha-multiply-duration-integer.html)
    There is no mixing of numeric types in Go.

20. [Go gotcha: Why is this index out of range?](gotcha-index-out-of-range.html)
    Arrays, slices and strings are indexed starting from zero.

21. [Go gotcha: Unexpected values in range loop](gotcha-unexpected-values-range.html)
    The range loop generates two values: first the index, then the data.

22. [Go gotcha: Can't change entries in range loop](gotcha-change-value-range.html)
    The range loop uses a local variable to store iteration values.

23. [Go gotcha: Iteration variable doesn't see change in range loop](gotcha-range-copy-array.html)
    The range expression is evaluated once before beginning the loop.

24. [Go gotcha: Iteration variables and closures](gotcha-data-race-closure.html)
    A data race occurs when two goroutines access the same variable concurrently and at least one of the accesses is a write.

25. [Go gotcha: Why is the JSON output empty?](gotcha-json-marshal-empty.html)
    Only the the exported fields of a Go struct will be present in the JSON output.

26. [Go gotcha: Why is nil not equal to nil?](gotcha-why-nil-error-not-equal-nil.html)
    An interface value is nil only if the concrete value and dynamic type are both nil.

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
