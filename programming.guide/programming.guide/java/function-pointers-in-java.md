



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

# Function Pointers in Java

Java does not provide function pointers in the same way C/C++ does.

Instead of passing a function pointer `f`, you create an object with an instance method `f` and pass the object instead. With lambdas and method refernecs the syntactical overhead for doing this is close to zero.

## Using a method reference

    class Example {
        // Method that takes a "method" as argument
        static void exampleMethod(Runnable toRun) {
            toRun.run();
        }

        // Method to pass
        static void sayHello() {
            System.out.println("Hello");
        }

        public static void main(String[] args) {
            exampleMethod(Example::sayHello);  // prints "Hello"
        }
    }

## Using a lambda

You may also invoke the `exampleMethod` above as follows:

    exampleMethod(() -> System.out.println("Hello"));

For similar examples with different method signatures, see the [Lambda Cheat Sheet](lambda-cheat-sheet.html).

## Using ordinary objects

The above examples requires Java 8. Here's how to do it in Java 7:

    exampleMethod(new Runnable() {
        @Override
        public void run() {
            System.out.println("Hello");
        }
    });

## Using reflection

You can use reflection to pass actual [`Method`](https://docs.oracle.com/javase/8/docs/api/java/lang/reflect/Method.html) objects and [`Method.invoke`](https://docs.oracle.com/javase/8/docs/api/java/lang/reflect/Method.html#invoke-java.lang.Object-java.lang.Object%3AA-) to invoke the method. This is not recommended and often seen as a hack / last resort.

    import java.lang.reflect.Method;

    class Example {

        static void exampleMethod(Method toInvoke) throws Exception {
            // null as callee for static methods
            toInvoke.invoke(null);
        }

        public static void sayHello() {
            System.out.println("Hello");
        }

        public static void main(String[] args) throws Exception {
            // prints "Hello"
            exampleMethod(Example.class.getMethod("sayHello"));
        }
    }

## A real world use case

Let's take a look at a more realistic use case.

**Example:** Storing "methods" in a hash map

    import java.util.*;

    class Example {

        public static void main(String[] args) {
            Map<Character, Runnable> commands = new HashMap<>();

            // Populate commands map
            commands.put('h', () -> System.out.println("Type h or q"));
            commands.put('q', () -> System.exit(0));

            while (true) {
                // Print menu
                System.out.println("Menu");
                System.out.println("h) Help");
                System.out.println("q) Quit");

                // User input
                char key = new Scanner(System.in).nextLine().charAt(0);

                // Run selected command
                if (commands.containsKey(key))
                    commands.get(key).run();
            }
        }
    }

## Comments (1)

![User avatar](https://www.gravatar.com/avatar/d41d8cd98f00b204e9800998ecf8427e?d=mp)

Awesome guide, many thanks

<span style="color: grey">by Felipe Amorim | </span> <span class="reply-button">Reply</span>

### Add comment

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
