<span class="underline"></span>

<span class="underline"></span>

Further Reading
---------------

[String handling cheat sheet](string-functions-reference-cheat-sheet.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Package fmt](https://golang.org/pkg/fmt)  
<span style="color: grey; font-style: italic; font-size: smaller">golang.org</span>

[Strings, bytes, runes and characters in Go](https://blog.golang.org/strings)  
<span style="color: grey; font-style: italic; font-size: smaller">The Go Blog</span>

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

Go: Print with fmt cheat sheet
==============================

A **format specifier** is a string that contains the text you want to format plus some placeholders, called **verbs**, that tell the functions in the [`fmt`](https://golang.org/pkg/fmt) package how to format your arguments.

In this example:

    fmt.Printf("Hex: %x.\n", 255) // Output: "Hex: ff."

-   the **format specifier** is `"Hex: %x.\n"`,
-   the **verb** `%x` formats `255` in base 16 notation, and
-   the **special value** `\n` is a line feed.

Use the special verb `%%`, which consumes no argument, to write a literal percent sign:

    fmt.Printf("%d %%", 50) // Output: "50 %"

Generic formatting
------------------

Argument: `[]int{1, 2}`

<table><thead><tr class="header"><th>Formatting</th><th>Description</th><th>Verb</th></tr></thead><tbody><tr class="odd"><td>[1 2]</td><td>Default format</td><td><code>%v</code></td></tr><tr class="even"><td>[]int{1, 2}</td><td>Go-syntax format</td><td><code>%#v</code></td></tr><tr class="odd"><td>[]int</td><td>The type of the value</td><td><code>%T</code></td></tr></tbody></table>

Integer
-------

Argument: `109`

<table><thead><tr class="header"><th>Formatting</th><th>Description</th><th>Verb</th></tr></thead><tbody><tr class="odd"><td>109</td><td>Base 10</td><td><code>%d</code></td></tr><tr class="even"><td>+109</td><td>Always show sign</td><td><code>%+d</code></td></tr><tr class="odd"><td>␣109</td><td>Width 4, right justify</td><td><code>%4d</code></td></tr><tr class="even"><td>109␣</td><td>Width 4, left justify</td><td><code>%-4d</code></td></tr><tr class="odd"><td>0109</td><td>Width 4, pad with zero</td><td><code>%04d</code></td></tr><tr class="even"><td>m</td><td>Character</td><td><code>%c</code></td></tr><tr class="odd"><td>'m'</td><td>Quoted character</td><td><code>%q</code></td></tr><tr class="even"><td>1101101</td><td>Base 2</td><td><code>%b</code></td></tr><tr class="odd"><td>155</td><td>Base 8</td><td><code>%o</code></td></tr><tr class="even"><td>6d</td><td>Base 16, lowercase</td><td><code>%x</code></td></tr><tr class="odd"><td>6D</td><td>Base 16, uppercase</td><td><code>%X</code></td></tr><tr class="even"><td>0x6d</td><td>Base 16, with leading 0x</td><td><code>%#x</code></td></tr><tr class="odd"><td>U+006D</td><td>Unicode</td><td><code>%U</code></td></tr><tr class="even"><td>U+006D 'm'</td><td>Unicode with character</td><td><code>%#U</code></td></tr></tbody></table>

Boolean
-------

Use `%t` to format a boolean as `true` or `false`.

Pointer
-------

Use `%p` to format a pointer in base 16 notation with leading `0x`.

Float
-----

Argument: `123.456`

<table><thead><tr class="header"><th>Formatting</th><th>Description</th><th>Verb</th></tr></thead><tbody><tr class="odd"><td>1.234560e+02</td><td>Scientific notation</td><td><code>%e</code></td></tr><tr class="even"><td>123.456000</td><td>Decimal point, no exponent</td><td><code>%f</code></td></tr><tr class="odd"><td>123.46</td><td>Default width, precision 2</td><td><code>%.2f</code></td></tr><tr class="even"><td>␣␣123.46</td><td>Width 8, precision 2</td><td><code>%8.2f</code></td></tr><tr class="odd"><td>123.456</td><td>Exponent as needed, necessary digits only</td><td><code>%g</code></td></tr></tbody></table>

String or byte slice
--------------------

Argument: `"café"`

<table><thead><tr class="header"><th>Formatting</th><th>Description</th><th>Verb</th></tr></thead><tbody><tr class="odd"><td>café</td><td>Plain string</td><td><code>%s</code></td></tr><tr class="even"><td>␣␣café</td><td>Width 6, right justify</td><td><code>%6s</code></td></tr><tr class="odd"><td>café␣␣</td><td>Width 6, left justify</td><td><code>%-6s</code></td></tr><tr class="even"><td>"café"</td><td>Quoted string</td><td><code>%q</code></td></tr><tr class="odd"><td>636166c3a9</td><td>Hex dump of byte values</td><td><code>%x</code></td></tr><tr class="even"><td>63 61 66 c3 a9</td><td>Hex dump with spaces</td><td><code>% x</code></td></tr></tbody></table>

Special values
--------------

<table><thead><tr class="header"><th>Value</th><th>Description</th></tr></thead><tbody><tr class="odd"><td><code>\a</code></td><td>U+0007 alert or bell</td></tr><tr class="even"><td><code>\b</code></td><td>U+0008 backspace</td></tr><tr class="odd"><td><code>\f</code></td><td>U+000C form feed</td></tr><tr class="even"><td><code>\n</code></td><td>U+000A line feed or newline</td></tr><tr class="odd"><td><code>\r</code></td><td>U+000D carriage return</td></tr><tr class="even"><td><code>\t</code></td><td>U+0009 horizontal tab</td></tr><tr class="odd"><td><code>\v</code></td><td>U+000b vertical tab</td></tr><tr class="even"><td><code>\\</code></td><td>U+005c backslash</td></tr></tbody></table>

Arbitrary values can be encoded with backslash escapes. There are four different formats:

-   `\x` followed by exactly two hexadecimal digits;
-   `\` followed by exactly three octal digits.
-   `\u` followed by exactly four hexadecimal digits;
-   `\U` followed by exactly eight hexadecimal digits;

The escapes `\u` and `\U` represent Unicode code points.

These special values can be used in any `""` string literal:

    fmt.Println("\\caf\u00e9") // Output: \café

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
