<span class="underline"></span>

<span class="underline"></span>

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

# Go: Bitwise operators cheat sheet

The binary number 00010000 can be written as `020`, `16` or `0x10`.

<table><thead><tr class="header"><th>Literal</th><th>Base</th><th>Note</th></tr></thead><tbody><tr class="odd"><td><code>020</code></td><td>8</td><td>Starts with <code>0</code></td></tr><tr class="even"><td><code>16</code></td><td>10</td><td>Never starts with <code>0</code>*</td></tr><tr class="odd"><td><code>0x10</code></td><td>16</td><td>Starts with <code>0x</code></td></tr></tbody></table>

`0` is an octal literal in Go.

## Built-in operators

<table><thead><tr class="header"><th>Operation</th><th>Result</th><th>Description</th></tr></thead><tbody><tr class="odd"><td><code>0011 &amp; 0101</code></td><td>0001</td><td>Bitwise AND</td></tr><tr class="even"><td><code>0011 | 0101</code></td><td>0111</td><td>Bitwise OR</td></tr><tr class="odd"><td><code>0011 ^ 0101</code></td><td>0110</td><td>Bitwise XOR</td></tr><tr class="even"><td><code>^0101</code></td><td>1010</td><td>Short for <code>1111 ^ 0101</code> (NOT)</td></tr><tr class="odd"><td><code>0011 &amp;^ 0101</code></td><td>0010</td><td>Bitclear (AND NOT)</td></tr><tr class="even"><td><code>00110101&lt;&lt;2</code></td><td>11010100</td><td>Left shift</td></tr><tr class="odd"><td><code>00110101&lt;&lt;100</code></td><td>00000000</td><td>No upper limit on shift count</td></tr><tr class="even"><td><code>00110101&gt;&gt;2</code></td><td>00001101</td><td>Right shift</td></tr></tbody></table>

- The binary numbers in the examples are for explanation only. Integer literals in Go must be specified in octal, decimal or hexadecimal.

- The bitwise operators take both signed and unsigned integers as input. The right-hand side of a shift operator, however, must be an unsigned integer.

- Shift operators implement arithmetic shifts if the left operand is a signed integer and logical shifts if it is an unsigned integer.

## Package [`math/bits`](https://golang.org/pkg/math/bits/)

<table><thead><tr class="header"><th>Operation</th><th>Result</th><th>Description</th></tr></thead><tbody><tr class="odd"><td><code>bits.OnesCount8(00101110)</code></td><td>4</td><td>Number of one bits (population count)</td></tr><tr class="even"><td><code>bits.Len8(00101110)</code></td><td>6</td><td>Bits required to represent number</td></tr><tr class="odd"><td><code>bits.Len8(00000000)</code></td><td>0</td><td></td></tr><tr class="even"><td><code>bits.LeadingZeros8(00101110)</code></td><td>2</td><td>Number of leading zero bits</td></tr><tr class="odd"><td><code>bits.LeadingZeros8(00000000)</code></td><td>8</td><td></td></tr><tr class="even"><td><code>bits.TrailingZeros8(00101110)</code></td><td>1</td><td>Number of trailing zero bits</td></tr><tr class="odd"><td><code>bits.TrailingZeros8(00000000)</code></td><td>8</td><td></td></tr><tr class="even"><td><code>bits.RotateLeft8(00101110, 3)</code></td><td>01110001</td><td>The value rotated left by 3 bits</td></tr><tr class="odd"><td><code>bits.RotateLeft8(00101110, -3)</code></td><td>11000101</td><td>The value rotated <strong>right</strong> by 3 bits</td></tr><tr class="even"><td><code>bits.Reverse8(00101110)</code></td><td>01110100</td><td>Bits in reversed order</td></tr><tr class="odd"><td><code>bits.ReverseBytes16(0x00ff)</code></td><td><code>0xff00</code></td><td>Bytes in reversed order</td></tr></tbody></table>

- These functions operate on **unsigned integers**.

- They come in different forms that take arguments of different sizes. For example, `Len`, `Len8`, `Len16`, `Len32`, and `Len64` apply to the types `uint`, `uint8`, `uint16`, `uint32`, and `uint64`, respectively.

- The functions are recognized by the compiler and on most architectures they are treated as intrinsics for additional performance.

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
