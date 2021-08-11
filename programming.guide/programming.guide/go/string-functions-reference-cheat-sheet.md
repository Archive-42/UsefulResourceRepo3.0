<span class="underline"></span>

<span class="underline"></span>

Further Reading
---------------

[What is a rune?](rune.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Strings, bytes, runes and characters in Go](https://blog.golang.org/strings)  
<span style="color: grey; font-style: italic; font-size: smaller">The Go Blog</span>

[Print with fmt cheat sheet](fmt-printf-reference-cheat-sheet.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Regular expressions](regexp-cheat-sheet.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

Top Go Articles
---------------

1.  [Go gotcha](go-gotcha.html)
2.  String handling cheat sheet
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

Go: String handling cheat sheet
===============================

String literals
---------------

<table><thead><tr class="header"><th>Expression</th><th>Result</th><th>Note</th></tr></thead><tbody><tr class="odd"><td><code>""</code></td><td></td><td>Empty string, zero value for <code>string</code></td></tr><tr class="even"><td><code>"Japan 日本"</code></td><td>Japan 日本</td><td>Go code is Unicode text encoded in UTF‑8</td></tr><tr class="odd"><td><code>"\xe6\x97\xa5"</code></td><td>日</td><td><code>\xNN</code> specifies a byte</td></tr><tr class="even"><td><code>"\u65E5"</code></td><td>日</td><td><code>\uNNNN</code> specifies a Unicode value</td></tr><tr class="odd"><td><code>`\xe6`</code></td><td>\xe6</td><td>Raw string literal*</td></tr></tbody></table>

In ``` `` ``` string literals, characters are interpreted literally: backslashes have no special meaning and the string may contain newlines.

Basic string handling
---------------------

<table><thead><tr class="header"><th>Expression</th><th>Result</th><th>Note</th></tr></thead><tbody><tr class="odd"><td><code>"Ja" + "pan"</code></td><td>Japan</td><td>Concatenation</td></tr><tr class="even"><td><code>"Japan" == "Japan"</code></td><td>true</td><td>Equality</td></tr><tr class="odd"><td><code>strings.EqualFold("Japan", "JAPAN")</code></td><td>true</td><td>Unicode case-folding</td></tr><tr class="even"><td><code>"japan" &lt; "Japan"</code></td><td>true</td><td>Lexical order</td></tr><tr class="odd"><td><code>len("日")</code></td><td>3</td><td>Length in bytes</td></tr><tr class="even"><td><code>utf8.RuneCountInString("日")</code></td><td>1</td><td>in runes <span class="tag">unicode/utf8</span></td></tr><tr class="odd"><td><code>utf8.ValidString("日")</code></td><td>true</td><td>UTF-8? <span class="tag">unicode/utf8</span></td></tr><tr class="even"><td><code>"Japan"[2]</code></td><td>'p'</td><td>Byte at postion 2</td></tr><tr class="odd"><td><code>"Japan"[1:3]</code></td><td>ap</td><td>Byte indexing</td></tr><tr class="even"><td><code>"Japan"[:2]</code></td><td>Ja</td><td></td></tr><tr class="odd"><td><code>"Japan"[2:]</code></td><td>pan</td><td></td></tr></tbody></table>

A Go [range loop](for-loop-range-array-slice-map-channel.html) iterates over UTF-8 encoded characters ([runes](rune.html)):

    for i, ch := range "Japan 日本" {
            fmt.Printf("%d:%q ", i, ch)
    }
    // Output: 0:'J' 1:'a' 2:'p' 3:'a' 4:'n' 5:' ' 6:'日' 9:'本'

Iterating over bytes produces nonsense characters for non-ASCII text:

    s := "Japan 日本"
    for i := 0; i < len(s); i++ {
            fmt.Printf("%q ", s[i])
    }
    // Output: 'J' 'a' 'p' 'a' 'n' ' ' 'æ' '\u0097' '¥' 'æ' '\u009c' '¬'

Find
----

<table><thead><tr class="header"><th>Expression</th><th>Result</th><th>Note</th></tr></thead><tbody><tr class="odd"><td><code>strings.Contains("Japan", "abc")</code></td><td>false</td><td>Is abc in Japan?</td></tr><tr class="even"><td><code>strings.ContainsAny("Japan", "abc")</code></td><td>true</td><td>Is a, b or c in Japan?</td></tr><tr class="odd"><td><code>strings.Count("Banana", "ana")</code></td><td>1</td><td>Non-overlapping instances of ana</td></tr><tr class="even"><td><code>strings.HasPrefix("Japan", "Ja")</code></td><td>true</td><td>Does Japan start with Ja?</td></tr><tr class="odd"><td><code>strings.HasSuffix("Japan", "pan")</code></td><td>true</td><td>Does Japan end with pan?</td></tr><tr class="even"><td><code>strings.Index("Japan", "abc")</code></td><td>-1</td><td>Index of first abc</td></tr><tr class="odd"><td><code>strings.IndexAny("Japan", "abc")</code></td><td>1</td><td>a, b or c</td></tr><tr class="even"><td><code>strings.LastIndex("Japan", "abc")</code></td><td>-1</td><td>Index of last abc</td></tr><tr class="odd"><td><code>strings.LastIndexAny("Japan", "abc")</code></td><td>3</td><td>a, b or c</td></tr></tbody></table>

Replace
-------

<table><thead><tr class="header"><th>Expression</th><th>Result</th><th>Note</th></tr></thead><tbody><tr class="odd"><td><code>strings.Replace("foo", "o", ".")</code></td><td>f..</td><td>Replace “o” with “.”</td></tr><tr class="even"><td><code>f := func(r rune) rune {                       return r + 1                   }                   strings.Map(f, "ab")</code></td><td>bc</td><td>Apply function to each character</td></tr><tr class="odd"><td><code>strings.ToUpper("Japan")</code></td><td>JAPAN</td><td>Uppercase</td></tr><tr class="even"><td><code>strings.ToLower("Japan")</code></td><td>japan</td><td>Lowercase</td></tr><tr class="odd"><td><code>strings.Title("ja pan")</code></td><td>Ja Pan</td><td>Initial letters to uppercase</td></tr><tr class="even"><td><code>strings.TrimSpace(" foo\n")</code></td><td>foo</td><td>Strip leading and trailing white space</td></tr><tr class="odd"><td><code>strings.Trim("foo", "fo")</code></td><td></td><td>Strip <em>leading and trailing</em> f:s and o:s</td></tr><tr class="even"><td><code>strings.TrimLeft("foo", "fo")</code></td><td>oo</td><td><em>only leading</em></td></tr><tr class="odd"><td><code>strings.TrimRight("foo", "fo")</code></td><td>f</td><td><em>only trailing</em></td></tr><tr class="even"><td><code>strings.TrimPrefix("foo", "fo")</code></td><td>o</td><td></td></tr><tr class="odd"><td><code>strings.TrimSuffix("foo", "o")</code></td><td>fo</td><td></td></tr></tbody></table>

Split and join
--------------

<table><thead><tr class="header"><th>Expression</th><th>Result</th><th>Note</th></tr></thead><tbody><tr class="odd"><td><code>strings.Fields(" a\t b\n")</code></td><td><code>["a" "b"]</code></td><td>Into substrings, remove white space</td></tr><tr class="even"><td><code>strings.Split("a:b", ":")</code></td><td><code>["a" "b"]</code></td><td>remove separator</td></tr><tr class="odd"><td><code>strings.SplitAfter("a:b", ":")</code></td><td><code>["a:" "b"]</code></td><td>keep separator</td></tr><tr class="even"><td><code>arr := []string{"a", "b"}</code><br />
<code>strings.Join(arr, ":")</code></td><td>a:b</td><td>Join strings, add separator</td></tr><tr class="odd"><td><code>strings.Repeat("da", 2)</code></td><td>dada</td><td>2 copies of “da”</td></tr></tbody></table>

Convert
-------

<table><thead><tr class="header"><th>Expression</th><th>Result</th><th>Note</th></tr></thead><tbody><tr class="odd"><td><code>strconv.Itoa(-42)</code></td><td><code>"-42"</code></td><td>Int to string</td></tr><tr class="even"><td><code>strconv.FormatInt(255, 16)</code></td><td><code>"ff"</code></td><td>Base 16</td></tr></tbody></table>

### Sprintf

The [`fmt.Sprintf`](https://golang.org/pkg/fmt/#Sprintf) function is often your best friend when converting data to string:

    s := fmt.Sprintf("%.4f", math.Pi) // s == "3.1416"

The [Print with fmt cheat sheet](fmt-printf-reference-cheat-sheet.html) explains the most common formatting flags.

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
