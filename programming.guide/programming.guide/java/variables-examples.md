



## Featured Stack Overflow Post

[In Java, difference between default, public, protected, and private](https://stackoverflow.com/a/33627846/276052)

[<img src="../images/so-featured-33627846.png" alt="StackOverflow screenshot thumbnail" class="screenshot" />](https://stackoverflow.com/a/33627846/276052)



## Top Java Articles

1.  [Do interfaces inherit from Object?](do-interfaces-inherit-from-object.html)
2.  [Executing code in comments?!](executing-code-in-comments.html)
3.  [Functional Interfaces](functional-interfaces.html)
4.  [Handling InterruptedException](handling-interrupted-exceptions.html)
5.  [Why wait must be called in a synchronized block](why-wait-must-be-in-synchronized.html)

[**See all 190 Java articles**](index.html)

## Top Algorithm Articles

1.  [Dynamic programming vs memoization vs tabulation](../dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](../big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](../sliding-window-example.html)
4.  [What makes a good loop invariant?](../what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](../random-point-within-circle.html)

# Java Variables (with examples)

You use a variable when you need to store a value and refer to it elsewhere in the code.

In the example below, the two variables are highlighted.

    String username = enterUsername();
    String password = enterPassword();
    if (login(username, password)) {
        System.out.println("Welcome " + username + "!");
    } else {
        System.out.println("Invalid username/password");
    }

## Declaring

To use a variable you must first _declare_ it. When you declare a variable you specify

- the **type** of data you will store in it,
- its **name** (or _identifier_), and,
- optionally, an **initial value**.

This code

    int maxLength = 100;

…means:

_From here on, let `maxLength` represent an integer (`int`). Initialize it with value `100`._

If you try to use a variable that hasn't been declared (e.g. if you misspell a variable name) the compiler will complain and say something like _"Identifier amxLength not found."_

### Multiple variables

You can declare multiple variables at once with the same type:

    int i, j, l;
    boolean y = true, n = false;

Most style guides however, recommend against this.

## Variable names…

- …are **case sensitive**.
- …may include **any unicode letter or digit**
- …**must not** start with a digit
- …**must not** be spelled the same way as a keyword, `true`, `false` or `null`
- …should by convention **start with a lower case letter** and be written in **camelCase**

## Types

You **must choose a type** for each variable. There's no such thing as an untyped variable in Java. The type must be respected throughout the code. This code would give you a compiler error:

    int i;
    i = true; // Can't store a boolean value in an integer variable

Types come in two shapes:

- **Primitive types** --- simple types used to hold numbers, characters, etc
- **Reference types** --- used to store references to objects, such as `Person`, `Car`, etc

See [Java: Primitives vs Objects and References](primitives-vs-objects-references.html) for further details.

Here are some examples, including all 8 primitive types:

    byte b;      // integers, −128–127
    short s;     // integers, ±32 thousand
    int i;       // integers, ±2 billion
    long l;      // integers, ±9 quintillion
    float f;     // reals, ~6 digits precision
    double d;    // reals, ~15 digits precision
    boolean z;   // true or false
    char c;      // character

    Person p;    // References to a Person objects
    Car v;       // References to a Car objects

### Which numeric type to choose?

**For integers**, use `int` unless you have reasons to use something else. Common exceptions: Unix timestamps and database IDs typically require `long`.

**For reals**, use `double` unless you have reasons to use something else. Common exceptions: Use [`BigDecimal`](https://docs.oracle.com/javase/8/docs/api/java/math/BigDecimal.html) if you want to avoid rounding errors, for instance when dealing with currency.

### Arrays

If you need to store, say 10 integers (but don't want to create 10 variables) you can use an **array**, or list. See [Java Arrays (with examples)](arrays.html) and [Java: Array vs ArrayList (and other Lists)](array-vs-arraylist.html).

For more information on the Java type system, see separate article: [Types in Java](types.html).

## Scope

If you for instance declare a variable in one method, you can't access that same variable in another method. Each variable has a **scope**; a section of code where it's accessible.

The scope is delimited by `{` and `}`.

` void method() {`

<span style="
                  position: absolute;
                  top: 0;
                  right: 0;
                  padding: 0.1em 0.3em;
                  font-size: smaller;
                  font-weight: bold;
                  color: blue;
                ">scope of d</span>

` double d;`

` …`

` if (…) {`

<span style="
                  position: absolute;
                  top: 0;
                  right: 0;
                  padding: 0.1em 0.3em;
                  font-size: smaller;
                  font-weight: bold;
                  color: #dd0000;
                ">scope of i</span>

` int i;`

` ` ` …`

` `

`} else {`

<span style="
                    position: absolute;
                    top: 0;
                    right: 0;
                    padding: 0.1em 0.3em;
                    font-size: smaller;
                    font-weight: bold;
                    color: green;
                  ">scope of s</span>

` String s;`

` ` ` …`

` ` `}`

` …`

` i = 17; // Error: i is out of scope`

` ` `}`

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
