



## Top Algorithm Articles

1.  [Dynamic programming vs memoization vs tabulation](dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](sliding-window-example.html)
4.  [What makes a good loop invariant?](what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](random-point-within-circle.html)

[**See all algorithm articles**](algorithms.html)



## Top Java Articles

1.  [Do interfaces inherit from Object?](java/do-interfaces-inherit-from-object.html)
2.  [Executing code in comments?!](java/executing-code-in-comments.html)
3.  [Functional Interfaces](java/functional-interfaces.html)
4.  [Handling InterruptedException](java/handling-interrupted-exceptions.html)
5.  [Why wait must be called in a synchronized block](java/why-wait-must-be-in-synchronized.html)

[**See all Java articles**](java/index.html)

# Statements vs Expressions

## Statements

A statement performs some **action**

## Expressions

An expression evaluates to some **value**

### Examples

    print("Hello World")

    sleep(1000)

    return 55

    if (done) exit()

    throw SomeError()

### Examples

    "Hello World"

    1000

    5 + 3

    a * 5 > b

    x_flag & mask

An expression can be part of a statement:

    while (x < 5)
        x += 15

    print("i: " + i)

A statement is never part of an expression.

In typed languages…

…statements typically don't have a type. If they do, the type is typically something like `Unit` or `void`.

…all expressions have types. `"Hello World"` is a string, `5 + 7` is an integer and so on.

## Details

Some expressions such as `i++` (unary increment in C-like languages) have side-effects and could be viewed as statements embedded in expressions: `while (i++ < 15) …`

Some things can be used both as expressions and statements. A call to a function returning a value for example. In C-like languages they need to be terminated by a `;` to form a complete statement.

    myFunction();                 // As statement
    if (myFunction())             // As expression
        print("Returned true!");

In scripting languages it's also common to use short circuiting boolean expressions. In shell scripting you often see things like

    compile_code || exit 1

or in PHP where the following is a common pattern

    fopen($site, "r") or die("Unable to connect");

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](terms-and-conditions.html)
