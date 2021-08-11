## Related

[Visit all files and folders in a directory tree](list-directory-recursive.html)  
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

# Go: List all files and folders in a directory

Use the [`ioutil.ReadDir`](https://golang.org/pkg/io/ioutil/#ReadDir) function in package [`io/ioutil`](https://golang.org/pkg/io/ioutil/). It returns a sorted slice containing elements of type [`os.FileInfo`](https://golang.org/pkg/os/#FileInfo).

The code in this example prints a sorted list of all file names in the current directory:

    files, err := ioutil.ReadDir(".")
    if err != nil {
            log.Fatal(err)
    }
    for _, f := range files {
            fmt.Println(f.Name())
    }

Example output:

    dev
    etc
    tmp
    usr

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
