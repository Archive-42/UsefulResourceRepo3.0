<span class="underline"></span>

<span class="underline"></span>

## Featured Stack Overflow Post

[In Java, difference between default, public, protected, and private](https://stackoverflow.com/a/33627846/276052)

[<img src="../images/so-featured-33627846.png" alt="StackOverflow screenshot thumbnail" class="screenshot" />](https://stackoverflow.com/a/33627846/276052)

<span class="underline"></span>

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

# 5 Java concepts explained: Overloading, overriding, shadowing, hiding, and obscuring

All five concepts are related to using **the same name for different things**.

## Overloading

Methods in the same class with the same name are called _overloaded_.

**Example:**

    class C {
        // Two overloaded methods
        void m(String s) { System.out.println("String: " + s); }
        void m(int i)    { System.out.println("int: " + i);    }
    }

This is ok as long as the methods differs in arity or type of formal parameters. Which method is called is determined by the compile time types of the arguments.

Real world example: There are 5 different versions of [`Math.abs`](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html).

## Overriding

Overriding has to do with inheritance. If `Dog` extends `Animal`, then method `Dog.eat()` _overrides_ `Animal.eat()`.

**Example:**

    class Animal {
        void eat() { System.out.println("Animal eating"); }
    }

    class Dog extends Animal {
        @Override
        void eat() { System.out.println("Dog eating"); }
    }

The `@Override` annotation is not mandatory but highly recommended.

In Java it's always the runtime type that determines which instance method is invked. So if an `Animal` variable `a` refers to a `Dog` object, `a.eat()` will invoke the overriding `Dog.eat` method.

## Shadowing

One variable _shadows_ another if they have the same name and are accessible in the same place.

**Example:**

    class C {
        int i = 0;

        void m() {
            int i = 1;
            System.out.println(iLocal variable shadows field.);


        }
    }

To access the field in the above example, you need to do `this.i`. Constructor parameters often shadow fields which is why you frequently see assignments such as `this.i = i;`.

Other things can be shadowed too. A local class can shadow a top-level class, a method in a local class can shadow a method in the enclosing class, and so on.

## Hiding

A field is said to _hide_ all fields with the same name in super classes.

**Example:**

    class Animal {
        int legs = 2;
    }

    class Dog extends Animal {
        int legsDog.legs hides Animal.legs = 4;


    }

You can use `super.legs` to access `Animal.legs` from within the `Dog` class.

Shadowing refers to scoping and import related clashes as opposed to hiding which refers to inheritance related clashes.

## Obscuring

If, for example, a local variable and a class share the same name, the precedence rules may render the class unusable. The class is said to be _obscured_ by the variable.

**Example:**

    class C {
        void m() {
            String System = "";
            System.out.println("Hello World");Will not compile. System is obscured by the local variable.

        }
    }

The above situation could be resolved by using the fully qualified name `java.lang.System`, or by statically importing `System.out`. If we happened to also have variables called `java` and `out`, neither of these workarounds would work and it would be impossible to access `System.out.println`.

## Comments (2)

![User avatar](https://www.gravatar.com/avatar/d41d8cd98f00b204e9800998ecf8427e?d=mp)

Well Explained

<span style="color: grey">by Calton | </span> <span class="reply-button">Reply</span>

![User avatar](https://www.gravatar.com/avatar/6bda4bb55b122a307c62310b0d42ed5d?d=mp)

Nice! I wish more tech folks were this succinct and "To-the-point".

<span style="color: grey">by Mohammed Manna | </span> <span class="reply-button">Reply</span>

### Add comment

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
