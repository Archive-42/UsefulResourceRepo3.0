



## Further Reading

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

# Go: Command-line arguments

The [`os.Args`](https://golang.org/pkg/os/#pkg-variables) variable holds the command-line arguments, starting with the program name:

    func main() {
            if len(os.Args) != 3 {
                    fmt.Println("Usage:", os.Args[0], "PATTERN", "FILE")
                    return
            }
            pattern := os.Args[1]
            file := os.Args[2]
            // ...
    }

    $ go build grep.go
    $ ./grep
    Usage: ./grep PATTERN FILE

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
