



## Related

[Write a command-line (CLI) application](write-command-line-application.html)  
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

# Go: Access environment variables

Use the [`os.Setenv`](https://golang.org/pkg/os/#Setenv), [`os.Getenv`](https://golang.org/pkg/os/#Getenv) and [`os.Unsetenv`](https://golang.org/pkg/os/#Unsetenv) functions to access environment variables:

    fmt.Printf("%q\n", os.Getenv("SHELL")) // "/bin/bash"

    os.Unsetenv("SHELL")
    fmt.Printf("%q\n", os.Getenv("SHELL")) // ""

    os.Setenv("SHELL", "/bin/dash")
    fmt.Printf("%q\n", os.Getenv("SHELL")) // "/bin/dash"

The [`os.Environ`](https://golang.org/pkg/os/#Environ) function returns a slice of `"key=value"` strings listing all environment variables.

    for _, s := range os.Environ() {
            kv := strings.SplitN(s, "=", 2) // unpacks "key=value"
            fmt.Printf("key:%q value:%q\n", kv[0], kv[1])
    }

    key:"SHELL" value:"/bin/bash"
    key:"SESSION" value:"ubuntu"
    key:"TERM" value:"xterm-256color"
    key:"LANG" value:"en_US.UTF-8"
    key:"XMODIFIERS" value:"@im=ibus"
    …

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
