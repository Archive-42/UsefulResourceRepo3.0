## Related

[Maps explained](maps-explained.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Implement a stack (LIFO)](implement-stack.html)  
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

# Go: How to implement a set

The idiomatic way to implement a set in Go is to use a **map**, where the keys in the map represent the elements in the set.

For simplicity `true` is typically used as dummy value.

Set operations are then encoded as operations on a map.

## Alternative representation

If the memory used by the booleans is an issue (which seems unlikely) you could replace them with empty structs. In Go, an empty struct typically doesn't require any memory.

Some set operations differ slighly. You typically declare…

    type void struct{}
    var member void

…and do the following:

<table><colgroup><col style="width: 50%" /><col style="width: 50%" /></colgroup><thead><tr class="header"><th>Operation</th><th>Code</th></tr></thead><tbody><tr class="odd"><td>Create empty set</td><td><p><code>mySet := make(map[string]bool)</code></p></td></tr><tr class="even"><td>Add an element</td><td><p><code>mySet["Foo"] = true</code></p></td></tr><tr class="odd"><td>Remove an element</td><td><p><code>delete(mySet, "Foo")</code></p></td></tr><tr class="even"><td>Iterate over a set</td><td><p><code>for e := range mySet { fmt.Println(e) }</code></p></td></tr><tr class="odd"><td>Size of set</td><td><p><code>size := len(mySet)</code></p></td></tr><tr class="even"><td>Check containment</td><td><p><code>exists := mySet["Foo"]</code></p></td></tr></tbody></table>

<table><colgroup><col style="width: 50%" /><col style="width: 50%" /></colgroup><thead><tr class="header"><th>Operation</th><th>Code</th></tr></thead><tbody><tr class="odd"><td>Create empty set</td><td><p><code>mySet := make(map[string]void)</code></p></td></tr><tr class="even"><td>Add an element</td><td><p><code>mySet["Foo"] = member</code></p></td></tr><tr class="odd"><td>Remove an element</td><td><p><code>delete(mySet, "Foo")</code></p></td></tr><tr class="even"><td>Iterate over a set</td><td><p><code>for e := range mySet { fmt.Println(e) }</code></p></td></tr><tr class="odd"><td>Size of set</td><td><p><code>size := len(mySet)</code></p></td></tr><tr class="even"><td>Check containment</td><td><p><code>_, exists := mySet["Foo"]</code></p></td></tr></tbody></table>

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
