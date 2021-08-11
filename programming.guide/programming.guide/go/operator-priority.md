## Further Reading

[Operators](operators.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Operators](https://golang.org/ref/spec#Operators)  
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

# Go: Operator precedence

## Unary operators

Unary operators have the highest precedence and bind the strongest.

## Binary operators

<table><thead><tr class="header"><th>Prio</th><th>Operators</th></tr></thead><tbody><tr class="odd"><td>1</td><td><code>*</code>  <code>/</code>  <code>%</code>  <code>&lt;&lt;</code>  <code>&gt;&gt;</code>  <code>&amp;</code>  <code>&amp;^</code></td></tr><tr class="even"><td>2</td><td><code>+</code>  <code>-</code>  <code>|</code>  <code>^</code></td></tr><tr class="odd"><td>3</td><td><code>==</code>  <code>!=</code>  <code>&lt;</code>  <code>&lt;=</code>  <code>&gt;</code>  <code>&gt;=</code></td></tr><tr class="even"><td>4</td><td><code>&amp;&amp;</code></td></tr><tr class="odd"><td>5</td><td><code>||</code></td></tr></tbody></table>

Among binary operators multiplication operators bind strongest, followed by addition operators, comparison operators, `&&` (logical and), and finally `||` (logical or).

Binary operators of the same precedence associate from **left to right**:

`x / y * z` is the same as `(x / y) * z`.

## Statement operators

The `++` and `--` operators **form statements** and fall outside the operator hierarchy:

`*p++` is the same as `(*p)++`.

## Examples

- `^a >> b` is the same as `(^a) >> b`
- `1 + 2*a[i]` is the same as `1 + (2*a[i])`
- `m == n+1 && <-ch > 0` is the same as `(m == (n+1)) && ((<-ch) > 0)`

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
