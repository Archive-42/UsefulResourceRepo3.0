



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

# Java: The 'this' reference (with examples)

Every ordinary (non-static) Java method runs in the context of an object, and `this` refers to that object.

If you have an object `myObj`, and you call `myObj.someMethod()` then `someMethod()` will run in the context of `myObj`.

**Example:** Printing the same object twice:

    class MyClass {
        public void printThis() {
            System.out.println(this);
        }
    }

    …
    MyClass obj = new MyClass();

    System.out.println(obj);  // prints "MyClass@4aa298b7"
    obj.printThis();          // prints "MyClass@4aa298b7"
    …

## When is the 'this' reference useful?

Sometimes there's a **name clash** between fields and local variables or arguments. It's especially common in constructors and setter methods.

**Example:** Disambiguating between fields and constructor arguments.

    class Person {

        String firstName;
        String lastName;

        public Person(String firstName, String lastName) {
            this.firstName = firstName;
            this.lastName = lastName;
        }
    }

You may also see it used when passing the current object **as an argument** to another method.

**Example:** Registering `this` object as a listener.

    class EventHandler implements EventListener {

        public EventHandler(EventSource source) {
            // Register this object as a listener
            source.registerListener(this);
        }

        @Overrride
        public void changeEvent(Event e) {
            // respond to event
        }
    }

There's also a more complex scenario where `this` is prefixed with a class to disambiguate between different static types. See article [Class.this explained](class-this.html)

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
