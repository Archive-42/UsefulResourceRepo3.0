<span class="underline"></span>

<span class="underline"></span>

## Related

[DZone: Marker Interface Isn't a Pattern or a Good Idea](https://dzone.com/articles/marker-interface-isnt-a-pattern-or-a-good-idea)  
<span style="color: grey; font-style: italic; font-size: smaller">by Erik Dietrich</span>

[Effective Java, Item 41: Use marker interfaces to define types](https://books.google.se/books?id=BIpDDwAAQBAJ)  
<span style="color: grey; font-style: italic; font-size: smaller">by Joshua Bloch</span>

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

# Java: Marker Interfaces

A **marker interface**, or **tag interface**, is an interface without any methods or fields. It's typically used to flag that instances of the implementing classes have some internal capability and behaves in a certain way when interacting with them.

It may also be the case that they have no semantical purpose other than to group related types together. It then serves as slightly more typesafe alternative to `Object` and can be seen as a poor man's substitute for discriminated union types.

## Examples from the Java API

[`RandomAccess`](https://docs.oracle.com/javase/8/docs/api/java/util/RandomAccess.html) is a marker interface that should be implemented by `List` classes that provide efficient non-sequential access. Specifically the Javadoc says:

> As a rule of thumb, a List implementation should implement this interface if, for typical instances of the class, this loop:
>
>     for (int i = 0, n = list.size(); i < n; i++)
>          list.get(i);
>
> runs faster than this loop:
>
>     for (Iterator i = list.iterator(); i.hasNext();)
>          i.next();

This allows clients to choose the most efficient code for traversing a given list. `ArrayList` implements this interface, while `LinkedList` does not.

**Note:** Since `RandomAccess` is intended specifically for lists, an alternative approach would have been to simply add a `boolean providesRandomAccess()` method to the `List` interface. However, at the time `RandomAccess` was introduced this was not an option, since `List` was already around, and adding methods to an interface is not a backward compatible change. Had this feature been introduced today on the other hand, a default method could have been a good alternative.

Other examples from the standard API:

<table><thead><tr class="header"><th>Interface</th><th>Purpose</th></tr></thead><tbody><tr class="odd"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/io/Serializable.html"><code>Serializable</code></a></td><td>Says that the object state may be serialized</td></tr><tr class="even"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/lang/Cloneable.html"><code>Cloneable</code></a></td><td>Says that <code>Object.clone</code> may perform a field-by-field copy of the object</td></tr><tr class="odd"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/rmi/Remote.html"><code>Remote</code></a></td><td>Says that methods may be invoked from a non-local virtual machine</td></tr><tr class="even"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/EventListener.html"><code>EventListener</code></a></td><td>Interface that all AWT event listeners must implement</td></tr><tr class="odd"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/nio/file/CopyOption.html"><code>CopyOption</code></a></td><td>Union type for <a href="https://docs.oracle.com/javase/8/docs/api/java/nio/file/LinkOption.html"><code>LinkOption</code></a> and <a href="https://docs.oracle.com/javase/8/docs/api/java/nio/file/StandardCopyOption.html"><code>StandardCopyOption</code></a></td></tr></tbody></table>

## A custom marker interface

Suppose we have a `LogUtil.logAsynchronously(Object o)` method that writes `o.toString()` to a log file. To return as quickly as possible from `logAsynchronously` we would like to call `toString` in the background thread. This is however only safe if other threads don't change the state of `o`. For this reason we add an `ImmutableObject` marker interface to allow for clients to opt in for this feature.

    interface ImmutableObject {}

The `logAsynchronously` method could then use `instanceof` as follows:

    class LogUtil {
        public void logAsynchronously(Object o) {
            if (o instanceof ImmutableObject) {
                runInBackground(() -> log(o.toString()));
            } else {
                String msg = o.toString();
                runInBackground(() -> log(msg));
            }
        }
        …
    }

## Use as discriminated union type

Other languages, such as F\# and TypeScript support _discriminated union types_ which means you can write things like:

    function print(value: string | number) {
        // value can be a string or a number
    }

Java does not provide support for this. If you want to express _"an instance of either `A` or `B`"_ you can create an empty interface `AorB` and let both classes implement this interface.

[`CopyOption`](https://docs.oracle.com/javase/8/docs/api/java/nio/file/CopyOption.html) is an example of this. It is an empty interface implemented by [`LinkOption`](https://docs.oracle.com/javase/8/docs/api/java/nio/file/LinkOption.html) and [`StandardCopyOption`](https://docs.oracle.com/javase/8/docs/api/java/nio/file/StandardCopyOption.html). This allows for methods such as [`Files.copy`](https://docs.oracle.com/javase/8/docs/api/java/nio/file/Files.html#copy-java.nio.file.Path-java.nio.file.Path-java.nio.file.CopyOption...-) to have a signature like this:

    public static Path copy(Path source,
                            Path target,
                            CopyOption... options) {
        …
    }

This approach doesn't let you create union types of classes out of your control, like `String` and `Number` as in the TypeScript example above. On the upside, you can easily extend the union type with new classes by letting more classes implement the empty interface.

## Restricting Use

By letting the marker interface, `M`, extend another interface, `I`, you make sure that `M` can only be implemented by classes that also implement `I`.

For example, `RandomAccess` is intendend to be used by `List` implementations. If the authors wanted to _enforce_ this, they could have implemented `RandomAccess` like this:

    interface RandomAccess extends List {}

## Criticism

The use of marker interfaces have long been criticized and nowadays most of the use cases are better solved with annotations.

Violates the principle of least astonishment  
The primary purpose of an interface is to establish a contract of communication. Since an empty interface is a contract that says nothing, it's at first glance quite useless. Some argue that marker interfaces aren't actual interfaces at all.

Forces a non-object oriented programming style  
The use of `instanceof` almost always begs the question: _Why isn't this solved with polymorphism / virtual methods?_ Where it would be natural to do

    obj.doSomething()

marker interfaces requires you to do

    if (obj instanceof Marker) {
        doSomething(obj);
    }

I.e. the logic is pushed outside the class itself. If this affects many places in the code, maintenance becomes a nightmare.

Requires casting  
If you have say, a `Cloneable` variable, you'd expect to be able to clone it. But no; You're forced to cast it to something else first. This is because the contract of a marker interface such as `Cloneable` is useless. All you get are the implicitly declared methods from `Object`, which is rarely what you're looking for. This ties back to the first item: Marker interfaces aren't proper interfaces at all.

Requires out of band knowledge  
If objects implementing marker interfaces requires special treatment, the programmer must be aware of this. Even if the programmer reads up on the documentation of the marker interface, it may be unclear where to be cautious. While an `Animal` doesn't implement the marker interface, a `Cat` might. Or some future—not yet known—subclass might. Or an undocumented anonymous subclass might.

## Marker Interfaces vs Annotations

Marker interfaces and annotations serve the same purpose: Convey metadata about the class to its consumers. The fundamental difference however, is that annotations are _meant_ to be used for this purpose, while interfaces are not.

Parameters  
A marker interface is like a boolean flag, while an annotation can carry an actual value. In other words, annotations let you express things like `@Author("John")`.

Inheritance  
Whether or not an annotation is inherited can be controlled through the [`@Inherited`](https://docs.oracle.com/javase/8/docs/api/java/lang/annotation/Inherited.html) annotation. Marker interfaces are always inherited and there's no way for subclasses to opt out. For example, if you extend a [`Serializable`](https://docs.oracle.com/javase/8/docs/api/java/io/Serializable.html) class, your class will automatically also be serializable.

Retention  
Sometimes the metadata is only relevant during compilation. Sometimes it should be available also in runtime. [`@Retention`](https://docs.oracle.com/javase/8/docs/api/java/lang/annotation/Retention.html) allows you to control this aspect for annotations. Marker interfaces are always available in runtime.

Applicability  
Marker interfaces can only be "applied" to classes and interfaces. Annotations can also be applied to methods, fields, local variables, parameters, packages and other annotations.

Repetition  
A marker interface can be applied at most once. Annotations can be applied multiple times. You can for example have multiple `@Author` annotations on the same class.

## When to use marker interfaces?

As shown above, annotations are superior in many ways. Marker interfaces however, give you something that annotations don't: **an actual type**. If (and only if) you need to express something like _"This method accepts an immutable value as argument"_ then you should use an `ImmutableValue` marker interface rather than an `@ImmutableValue` annotation. (You _can_ actually still use an annotation for this, but you would need to use a compiler plugin like the [Checker Framework](https://checkerframework.org/).)

**Rule of thumb:** Use marker interfaces if you want to define a type, otherwise use an annotation.

The [`EventListener`](https://docs.oracle.com/javase/8/docs/api/java/awt/EventListener.html) interface is an example where an annotation would not have been sufficient. Most annotations (even non-repeating, inherited, without arguments) would not have been suitable as a marker interface: [`@NotNull`](https://docs.oracle.com/javaee/7/api/javax/validation/constraints/NotNull.html), [`@JsonIgnore`](https://fasterxml.github.io/jackson-annotations/javadoc/2.5/com/fasterxml/jackson/annotation/JsonIgnore.html), [`@Interned`](https://checkerframework.org/api/org/checkerframework/checker/interning/qual/Interned.html) to mention a few.

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
