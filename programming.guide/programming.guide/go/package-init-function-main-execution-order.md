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

# Go: Package initialization and program execution order

## In a nutshell

- First the `main` package is initialized
- Imported packages are initialized before the package itself.
- Packages are initialized one at a time:
  - first package-level variables are initialized in declaration order,
  - then the `init` functions are run.
- The `main` function is called.

## Program execution

Program execution begins by initializing the `main` package and then calling the function `main`. When `main` returns, the program exits. It does **not wait** for other goroutines to complete.

## Package initialization

- Package-level variables are initialized in **declaration order**, but after any of the variables they **depend** on.

- Initialization of variables declared in multiple files is done in **lexical file name order**. Variables declared in the first file are declared before any of the variables declared in the second file.

- Initialization cycles are **not allowed**.

- Dependency analysis is performed **per package**; only references referring to variables, functions, and methods declared in the current package are considered.

**Example:** In this example (from the [Go language specification](https://golang.org/ref/spec#Package_initialization))…

    var (
            a = c + b
            b = f()
            c = f()
            d = 3
    )

    func f() int {
            d++
            return d
    }

…the initialization order is `d`, `b`, `c`, `a`.

## Init function

Variables may also be initialized using `init` functions:

    func init() { … }

Multiple such functions may be defined. They cannot be called from inside a program.

- A package with **no imports** is initialized
- by assigning initial values to all its package-level variables,
- followed by calling all `init` functions in the order they appear in the source.

- Imported packages are initialized before the package itself.

- Each package is initialized **once**, regardless if it's imported by multiple other packages.

It follows that there can be **no cyclic dependencies**.

Package initialization happens in a single goroutine, sequentially, one package at a time.

## Warning

Lexical ordering according to file names is not part of the formal language specification:

To ensure reproducible initialization behavior, build systems are encouraged to present multiple files belonging to the same package in lexical file name order to a compiler.  
<a href="https://golang.org/ref/spec#Package_initialization" class="quote-source">The Go Programming Language Specification: Package initialization</a>

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
