<span class="underline"></span>

<span class="underline"></span>

## Further reading

[How to Write Go Code](https://golang.org/doc/code.html)  
<span style="color: grey; font-style: italic; font-size: smaller">The Go Programming Language</span>

[Package documentation](package-documentation.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Library package example](library-package-example-template.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[How should I manage package versions using "go get"?](https://golang.org/doc/faq#get_version)  
<span style="color: grey; font-style: italic; font-size: smaller">The Go FAQ</span>

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

# Go: Packages explained

Every Go program is made up of packages and each package has an **import path**:

- `"fmt"`
- `"math/rand"`
- `"github.com/yourbasic/graph"`

Packages in the standard library have short import paths, such as `"fmt"` and `"math/rand"`.

Third-party packages, such as `"github.com/yourbasic/graph"`, typically have an import path that includes a hosting service (`github.com`) and an organization name (`yourbasic`).

By convention, the **package name** is the same as the last element of the import path:

- `fmt`
- `rand`
- `graph`

References to other packages' definitions must always be prefixed with their package names, and only the capitalized names from other packages are accessible.

    package main

    import (
            "fmt"
            "math/rand"

            "github.com/yourbasic/graph"
    )

    func main() {
            n := rand.Intn(100)
            g := graph.New(n)
            fmt.Println(g)
    }

## Declaring a package

Every Go source file starts with a package declaration, which contains only the package name.

For example, the file [`src/math/rand/exp.go`](https://golang.org/src/math/rand/exp.go), which is part of the implementation of the [`math/rand`](https://golang.org/pkg/math/rand/) package, contains the following code:

    package rand

    import "math"

    const re = 7.69711747013104972
    …

You don't need to worry about package name collisions, only the import path of a package must be unique. [How to Write Go Code](https://golang.org/doc/code.html) shows how to organize your code and its packages in a file structure.

## Package name conflicts

You can customize the name under which you refer to an imported package:

    package main

    import (
            csprng "crypto/rand"
            prng "math/rand"

            "fmt"
    )

    func main() {
            n := prng.Int() // pseudorandom number
            b := make([]byte, 8)
            csprng.Read(b) // cryptographically secure pseudorandom number
            fmt.Println(n, b)
    }

## Dot imports

If a period `.` appears instead of a name in an import statement, all the package's exported identifiers can be accessed without a qualifier.

    package main

    import (
            "fmt"
            . "math"
    )

    func main() {
            fmt.Println(Sin(Pi/2)*Sin(Pi/2) + Cos(Pi)/2)
    }

Dot imports can make programs hard to read and **generally should be avoided**.

## Package download

The [`go get`](https://golang.org/cmd/go/#hdr-Download_and_install_packages_and_dependencies) command downloads packages named by import paths, along with their dependencies, and then installs the packages:

    $ go get github.com/yourbasic/graph

The import path corresponds to the repository hosting the code. This reduces the likelihood of future name collisions.

The [Go Wiki](https://github.com/golang/go/wiki/Projects) and [Awesome Go](https://github.com/avelino/awesome-go) provide lists of high-quality Go packages and resources.

For more information on using remote repositories with the go tool, see [Command go: Remote import paths](https://golang.org/cmd/go/#hdr-Remote_import_paths).

## Package documentation

The [GoDoc](https://godoc.org/) web site hosts documentation for Go packages on Bitbucket, GitHub, Google Project Hosting and Launchpad:

- [`https://godoc.org/fmt`](https://godoc.org/fmt)
- [`https://godoc.org/math/rand`](https://godoc.org/math/rand)
- [`https://godoc.org/github.com/yourbasic/graph`](https://godoc.org/github.com/yourbasic/graph)

The [godoc](https://godoc.org/golang.org/x/tools/cmd/godoc) command extracts and generates documentation for all locally installed Go programs:

    $ godoc -http=:6060 &

starts a web server that presents the documentation at `http://localhost:6060/`.

For more on how to access and create documentation, see [Go: Package documentation](https://programming.guide/go/generate-download-documentation.html)

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
