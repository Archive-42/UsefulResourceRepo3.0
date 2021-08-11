<span class="underline"></span>

<span class="underline"></span>

## Related

[String handling cheat sheet](string-functions-reference-cheat-sheet.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[RE2 syntax](https://github.com/google/re2/wiki/Syntax)  
<span style="color: grey; font-style: italic; font-size: smaller">Google open source</span>

[Regular expression matching can be simple and fast](https://swtch.com/~rsc/regexp/regexp1.html)  
<span style="color: grey; font-style: italic; font-size: smaller">by Russ Cox</span>

[Time complexity explained](../time-complexity-explained.html)  
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

# Go: Regular expressions

- [Basics](regexp-cheat-sheet.html#basics)
- [Cheat sheet](regexp-cheat-sheet.html#cheat-sheet)
  - [Choice and grouping](regexp-cheat-sheet.html#choice-and-grouping)
  - [Repetition](regexp-cheat-sheet.html#repetition)
  - [Character classes](regexp-cheat-sheet.html#character-classes)
  - [Special characters](regexp-cheat-sheet.html#special-characters)
  - [Text boundary anchors](regexp-cheat-sheet.html#text-boundary-anchors)
- [Code examples](regexp-cheat-sheet.html#code-examples)
  - [First match](regexp-cheat-sheet.html#first-match)
  - [Location](regexp-cheat-sheet.html#location)
  - [All matches](regexp-cheat-sheet.html#all-matches)
  - [Replace](regexp-cheat-sheet.html#replace)
  - [Split](regexp-cheat-sheet.html#split)
- [Implementation](regexp-cheat-sheet.html#implementation)

## Basics

The regular expression `a.b` matches any string that starts with an `a`, ends with a `b`, and has a single character in between (the period matches any character).

To check if there is a **substring** matching `a.b`, write:

    matched, err := regexp.MatchString(`a.b`, "aaxbb")
    fmt.Println(matched) // true
    fmt.Println(err)     // nil (regexp is valid)

To check if a **full string** matches `a.b`, _anchor_ the start and the end:

- the caret `^` matches the beginning of a text or line,
- the dollar sign `$` matches the end of a text.

<!-- -->

    matched, _ := regexp.MatchString(`^a.b$`, "aaxbb")
    fmt.Println(matched) // false

Similarly, we can check if a string **starts with** or **ends with** a pattern by using only the start or end anchor.

For more complicated queries, **compile** the regular expression to create a [`Regexp`](https://golang.org/pkg/regexp/#Regexp) object. There are two options:

    re, err := regexp.Compile(`regexp`) // error if regexp invalid

    re := regexp.MustCompile(`regexp`) // panic if regexp invalid

It's convenient to use `raw strings` when writing regular expressions; both ordinary string literals and regular expressions use backslashes for special characters.

## Cheat sheet

### Choice and grouping

<table><thead><tr class="header"><th>Regexp</th><th>Meaning</th></tr></thead><tbody><tr class="odd"><td><code>xy</code></td><td><code>x</code> followed by <code>y</code></td></tr><tr class="even"><td><code>x|y</code></td><td><code>x</code> or <code>y</code>, prefer <code>x</code></td></tr><tr class="odd"><td><code>xy|z</code></td><td>same as <code>(xy)|z</code></td></tr><tr class="even"><td><code>xy*</code></td><td>same as <code>x(y*)</code></td></tr></tbody></table>

### Repetition

<table><thead><tr class="header"><th>Regexp</th><th>Meaning</th></tr></thead><tbody><tr class="odd"><td><code>x*</code></td><td>zero or more x, prefer more</td></tr><tr class="even"><td><code>x*?</code></td><td>prefer fewer</td></tr><tr class="odd"><td><code>x+</code></td><td>one or more x, prefer more</td></tr><tr class="even"><td><code>x+?</code></td><td>prefer fewer</td></tr><tr class="odd"><td><code>x?</code></td><td>zero or one x, prefer one</td></tr><tr class="even"><td><code>x??</code></td><td>prefer zero</td></tr><tr class="odd"><td><code>x{n}</code></td><td>exactly n x</td></tr></tbody></table>

### Character classes

<table><thead><tr class="header"><th>Expression</th><th>Meaning</th></tr></thead><tbody><tr class="odd"><td><code>.</code></td><td>any character</td></tr><tr class="even"><td><code>[ab]</code></td><td>the character a or b</td></tr><tr class="odd"><td><code>[^ab]</code></td><td>any character except a or b</td></tr><tr class="even"><td><code>[a-z]</code></td><td>any character from a to z</td></tr><tr class="odd"><td><code>[a-z0-9]</code></td><td>any character from a to z or 0 to 9</td></tr><tr class="even"><td><code>\d</code></td><td>a digit: <code>[0-9]</code></td></tr><tr class="odd"><td><code>\D</code></td><td>a non-digit: <code>[^0-9]</code></td></tr><tr class="even"><td><code>\s</code></td><td>a whitespace character: <code>[\t\n\f\r ]</code></td></tr><tr class="odd"><td><code>\S</code></td><td>a non-whitespace character: <code>[^\t\n\f\r ]</code></td></tr><tr class="even"><td><code>\w</code></td><td>a word character: <code>[0-9A-Za-z_]</code></td></tr><tr class="odd"><td><code>\W</code></td><td>a non-word character: <code>[^0-9A-Za-z_]</code></td></tr><tr class="even"><td><code>\p{Greek}</code></td><td>Unicode character class*</td></tr><tr class="odd"><td><code>\pN</code></td><td>one-letter name</td></tr><tr class="even"><td><code>\P{Greek}</code></td><td>negated Unicode character class*</td></tr><tr class="odd"><td><code>\PN</code></td><td>one-letter name</td></tr></tbody></table>

- [RE2: Unicode character class names](https://github.com/google/re2/wiki/Syntax)

### Special characters

To match a **special character** `\^$.|?*+-[]{}()` literally, escape it with a backslash. For example `\{` matches an opening brace symbol. Other escape sequences are:

<table><thead><tr class="header"><th>Symbol</th><th>Meaning</th></tr></thead><tbody><tr class="odd"><td><code>\t</code></td><td>horizontal tab = <code>\011</code></td></tr><tr class="even"><td><code>\n</code></td><td>newline = <code>\012</code></td></tr><tr class="odd"><td><code>\f</code></td><td>form feed = <code>\014</code></td></tr><tr class="even"><td><code>\r</code></td><td>carriage return = <code>\015</code></td></tr><tr class="odd"><td><code>\v</code></td><td>vertical tab = <code>\013</code></td></tr><tr class="even"><td><code>\123</code></td><td>octal character code (up to three digits)</td></tr><tr class="odd"><td><code>\x7F</code></td><td>hex character code (exactly two digits)</td></tr></tbody></table>

### Text boundary anchors

<table><thead><tr class="header"><th>Symbol</th><th>Matches</th></tr></thead><tbody><tr class="odd"><td><code>\A</code></td><td>at beginning of text</td></tr><tr class="even"><td><code>^</code></td><td>at beginning of text or line</td></tr><tr class="odd"><td><code>$</code></td><td>at end of text</td></tr><tr class="even"><td><code>\z</code></td><td></td></tr><tr class="odd"><td><code>\b</code></td><td>at ASCII word boundary</td></tr><tr class="even"><td><code>\B</code></td><td>not at ASCII word boundary</td></tr></tbody></table>

## Code examples

### First match

Use the [`FindString`](https://golang.org/pkg/regexp/#Regexp.FindString) method to find the **text of the first match**. If there is no match, the return value is an empty string.

    re := regexp.MustCompile(`foo.?`)
    fmt.Printf("%q\n", re.FindString("seafood fool")) // "food"
    fmt.Printf("%q\n", re.FindString("meat"))         // ""

### Location

Use the [`FindStringIndex`](https://golang.org/pkg/regexp/#Regexp.FindStringIndex) method to find `loc`, the **location of the first match**, in a string `s`. The match is at `s[loc[0]:loc[1]]`. A return value of nil indicates no match.

    re := regexp.MustCompile(`ab?`)
    fmt.Println(re.FindStringIndex("tablett"))    // [1 3]
    fmt.Println(re.FindStringIndex("foo") == nil) // true

### All matches

Use the [`FindAllString`](https://golang.org/pkg/regexp/#Regexp.FindAllString) method to find the **text of all matches**. A return value of nil indicates no match.

The method takes an integer argument `n`; if `n >= 0`, the function returns at most `n` matches.

    re := regexp.MustCompile(`a.`)
    fmt.Printf("%q\n", re.FindAllString("paranormal", -1)) // ["ar" "an" "al"]
    fmt.Printf("%q\n", re.FindAllString("paranormal", 2))  // ["ar" "an"]
    fmt.Printf("%q\n", re.FindAllString("graal", -1))      // ["aa"]
    fmt.Printf("%q\n", re.FindAllString("none", -1))       // [] (nil slice)

### Replace

Use the [`ReplaceAllString`](https://golang.org/pkg/regexp/#Regexp.ReplaceAllString) method to **replace the text of all matches**. It returns a copy, replacing all matches of the regexp with a replacement string.

    re := regexp.MustCompile(`ab*`)
    fmt.Printf("%q\n", re.ReplaceAllString("-a-abb-", "T")) // "-T-T-"

### Split

Use the [`Split`](https://golang.org/pkg/regexp/#Regexp.Split) method to **slice a string into substrings** separated by the regexp. It returns a slice of the substrings between those expression matches. A return value of nil indicates no match.

The method takes an integer argument `n`; if `n >= 0`, the function returns at most `n` matches.

    a := regexp.MustCompile(`a`)
    fmt.Printf("%q\n", a.Split("banana", -1)) // ["b" "n" "n" ""]
    fmt.Printf("%q\n", a.Split("banana", 0))  // [] (nil slice)
    fmt.Printf("%q\n", a.Split("banana", 1))  // ["banana"]
    fmt.Printf("%q\n", a.Split("banana", 2))  // ["b" "nana"]

    zp := regexp.MustCompile(`z+`)
    fmt.Printf("%q\n", zp.Split("pizza", -1)) // ["pi" "a"]
    fmt.Printf("%q\n", zp.Split("pizza", 0))  // [] (nil slice)
    fmt.Printf("%q\n", zp.Split("pizza", 1))  // ["pizza"]
    fmt.Printf("%q\n", zp.Split("pizza", 2))  // ["pi" "a"]

> **More functions:** There are 16 functions following the naming pattern
>
>     Find(All)?(String)?(Submatch)?(Index)?
>
> For example: `Find`, `FindAllString`, `FindStringIndex`, …

## Implementation

- The [`regexp`](https://golang.org/pkg/regexp/) package implements regular expressions with [RE2](https://golang.org/s/re2syntax) syntax.
- It supports UTF-8 encoded strings and Unicode character classes.
- The implementation is very efficient: the running time is linearly proportional to the size of the input.
- Backreferences are not supported since they cannot be efficiently implemented. Further reading: [Regular expression matching can be simple and fast (but is slow in Java, Perl, PHP, Python, Ruby, …)](https://swtch.com/~rsc/regexp/regexp1.html).

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
