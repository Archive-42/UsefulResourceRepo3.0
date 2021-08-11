<span class="underline"></span>

<span class="underline"></span>

Further Reading
---------------

[Operator precedence](operator-priority.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Operators](https://golang.org/ref/spec#Operators)  
<span style="color: grey; font-style: italic; font-size: smaller">The Go Programming Language Specification</span>

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

Go: Operators
=============

-   [Arithmetic](operators.html#arithmetic)
-   [Comparison](operators.html#comparison)
-   [Logical](operators.html#logical)
-   [Others](operators.html#others)

*See [Operator precedence](operator-priority.html) for evaluation order.*

Arithmetic
----------

<table><thead><tr class="header"><th style="text-align: center;">Operator</th><th>Name</th><th>Types</th></tr></thead><tbody><tr class="odd"><td style="text-align: center;">+</td><td>sum</td><td>integers, floats, complex values, strings</td></tr><tr class="even"><td style="text-align: center;">-</td><td>difference</td><td>integers, floats, complex values</td></tr><tr class="odd"><td style="text-align: center;">*</td><td>product</td><td>integers, floats, complex values</td></tr><tr class="even"><td style="text-align: center;">/</td><td>quotient</td><td>integers, floats, complex values</td></tr><tr class="odd"><td style="text-align: center;">%</td><td>remainder</td><td>integers</td></tr><tr class="even"><td style="text-align: center;">&amp;</td><td>bitwise AND</td><td>integers</td></tr><tr class="odd"><td style="text-align: center;">|</td><td>bitwise OR</td><td>integers</td></tr><tr class="even"><td style="text-align: center;">^</td><td>bitwise XOR</td><td>integers</td></tr><tr class="odd"><td style="text-align: center;">&amp;^</td><td>bit clear (AND NOT)</td><td>integers</td></tr><tr class="even"><td style="text-align: center;">&lt;&lt;</td><td>left shift</td><td>integer &lt;&lt; unsigned integer</td></tr><tr class="odd"><td style="text-align: center;">&gt;&gt;</td><td>right shift</td><td>integer &gt;&gt; unsigned integer</td></tr></tbody></table>

See [Arithmetic operators](https://golang.org/ref/spec#Arithmetic_operators) in the Go language specification for complete definitions of the shift, quotient and remainder operators, integer overflow, and floating point behavior.

Comparison
----------

Comparison operators compare two operands and yield an untyped boolean value.

<table><thead><tr class="header"><th>Operator</th><th>Name</th><th>Types</th></tr></thead><tbody><tr class="odd"><td>==</td><td>equal</td><td>comparable</td></tr><tr class="even"><td>!=</td><td>not equal</td><td>comparable</td></tr><tr class="odd"><td>&lt;</td><td>less</td><td>integers, floats, strings</td></tr><tr class="even"><td>&lt;=</td><td>less or equal</td><td>integers, floats, strings</td></tr><tr class="odd"><td>&gt;</td><td>greater</td><td>integers, floats, strings</td></tr><tr class="even"><td>&gt;=</td><td>greater or equal</td><td>integers, floats, strings</td></tr></tbody></table>

-   Boolean, integer, floats, complex values and strings are comparable.
-   Strings are ordered lexically byte-wise.
-   Two pointers are equal if they point to the same variable or if both are nil.
-   Two channel values are equal if they were created by the same call to make or if both are nil.
-   Two interface values are equal if they have identical dynamic types and equal concrete values or if both are nil.
-   A value x of non-interface type X and a value t of interface type T are equal if t's dynamic type is identical to X and t's concrete value is equal to x.
-   Two struct values are equal if their corresponding non-blank fields are equal.
-   Two array values are equal if their corresponding elements are equal.

Logical
-------

Logical operators apply to boolean values. The right operand is evaluated conditionally.

<table><thead><tr class="header"><th>Operator</th><th>Name</th><th>Description</th></tr></thead><tbody><tr class="odd"><td>&amp;&amp;</td><td>conditional AND</td><td>p &amp;&amp; q denotes "if p then q else false"</td></tr><tr class="even"><td>||</td><td>conditional OR</td><td>p || q denotes "if p then true else q"</td></tr><tr class="odd"><td>!</td><td>NOT</td><td>!p denotes "not p"</td></tr></tbody></table>

Others
------

<table><thead><tr class="header"><th>Operator</th><th>Name</th><th>Description</th></tr></thead><tbody><tr class="odd"><td>&amp;</td><td>address of</td><td>&amp;x generates a pointer to x</td></tr><tr class="even"><td>*</td><td>pointer indirection</td><td>*x denotes the variable pointed to by x</td></tr><tr class="odd"><td>&lt;-</td><td>receive</td><td>&lt;-ch is the value received from channel ch</td></tr></tbody></table>

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
