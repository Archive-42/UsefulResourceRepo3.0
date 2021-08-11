<span class="underline"></span>

<span class="underline"></span>

## Related

[List all files and folders in a directory](list-files-in-directory.html)  
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

# Go: Visit all files and folders in a directory tree

Use the [`filepath.Walk`](https://golang.org/pkg/path/filepath/#Walk) function in package [`path/filepath`](https://golang.org/pkg/path/filepath/):

- It walks a file tree calling a function of type [`filepath.WalkFunc`](https://golang.org/pkg/path/filepath/#WalkFunc) for each file or directory in the tree, including the root.
- The files are walked in lexical order.
- Symbolic links are not followed.

The code in this example lists the paths and sizes of all files and directories in the file tree rooted at the current directory:

    err := filepath.Walk(".", func(path string, info os.FileInfo, err error) error {
            if err != nil {
                    return err
            }
            fmt.Println(path, info.Size())
            return nil
    })
    if err != nil {
            log.Println(err)
    }

Example output:

    . 1644
    dev 1644
    dev/null 0
    dev/random 0
    dev/urandom 0
    dev/zero 0
    etc 1644
    etc/group 116
    etc/hosts 20
    etc/passwd 0
    etc/resolv.conf 0
    tmp 548
    usr 822
    usr/local 822
    usr/local/go 822
    usr/local/go/lib 822
    usr/local/go/lib/time 822
    usr/local/go/lib/time/zoneinfo.zip 366776

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
