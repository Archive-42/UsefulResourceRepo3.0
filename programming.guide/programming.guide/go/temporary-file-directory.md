



## Related

[Defer statement](defer.html)  
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

# Go: Create a temporary file or directory

## File

Use [`ioutil.TempFile`](https://golang.org/pkg/io/ioutil/#TempFile) in package [`io/ioutil`](https://golang.org/pkg/io/ioutil/) to create a temporary file:

    file, err := ioutil.TempFile("dir", "prefix")
    if err != nil {
            log.Fatal(err)
    }
    defer os.Remove(file.Name())

    fmt.Println(file.Name()) // For example "dir/prefix054003078"

The call to [`ioutil.TempFile`](https://golang.org/pkg/io/ioutil/#TempFile)

- creates a new file with a name starting with `"prefix"`
- in the directory `"dir"`,
- opens the file for reading and writing,
- and returns the new [`*os.File`](https://golang.org/pkg/os/#File).

To put the new file in [`os.TempDir()`](https://golang.org/pkg/os/#TempDir), the default directory for temporary files, call [`ioutil.TempFile`](https://golang.org/pkg/io/ioutil/#TempFile) with an empty directory string.

## Directory

Use [`ioutil.TempDir`](https://golang.org/pkg/io/ioutil/#TempDir) in package [`io/ioutil`](https://golang.org/pkg/io/ioutil/) to create a temporary directory:

    dir, err := ioutil.TempDir("dir", "prefix")
    if err != nil {
            log.Fatal(err)
    }
    defer os.RemoveAll(dir)

The call to [`ioutil.TempDir`](https://golang.org/pkg/io/ioutil/#TempDir)

- creates a new directory with a name starting with `"prefix"`
- in the directory `"dir"`,
- and returns the path of the new directory.

To put the new directory in [`os.TempDir()`](https://golang.org/pkg/os/#TempDir), the default directory for temporary files, call [`ioutil.TempDir`](https://golang.org/pkg/io/ioutil/#TempDir) with an empty directory string.

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
