



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

# Go: Current working directory

- Use [`os.Executable`](https://golang.org/pkg/os/#Executable) to find the path name for the executable that started the current process.

- Use [`filepath.Dir`](https://golang.org/pkg/path/filepath/#Dir) in package [`path/filepath`](https://golang.org/pkg/path/filepath/) to extract the path's directory.

<!-- -->

    path, err := os.Executable()
    if err != nil {
            log.Printf(err)
    }
    dir := filepath.Dir(path)
    fmt.Println(path) // For example /home/user/main
    fmt.Println(dir)  // For example /home/user

**Warning:** There is no guarantee that the path is still pointing to the correct executable. If a symlink was used to start the process, depending on the operating system, the result might be the symlink or the path it pointed to. If a stable result is needed, [`path/filepath.EvalSymlinks`](https://golang.org/pkg/path/filepath/#EvalSymlinks) might help.

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
