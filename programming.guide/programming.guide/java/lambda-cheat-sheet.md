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

# Java: Lambda Cheat Sheet

## Lambdas

    () -> "Hello"
    () -> System.out.println("Hello")
    (String str) -> str.length()
    (str) -> str.length()
    str -> str.length()
    (int i, int j) -> i + j
    (i, j) -> i + j

    () -> {
        System.out.println("Hello");
        System.out.println("World");
    }

    (int i) -> {
        System.out.println("Hello");
        return i;
    }

## Method References

    // Static methods
    Supplier<Thread> runtimeSup = Thread::currentThread;

    // Bound instance methods
    Supplier<String> helloSup = "hello"::toUpperCase;
    Consumer<String> printer = System.out::println;

    // Unbound instance methods
    Function<String, String> lower = String::toLowerCase;

    // Constructors
    Supplier<String> stringSup = String::new;
    Function<Integer, int[]> arrSup = int[]::new;

## Standard Functional Interfaces

<table><thead><tr class="header"><th>Interface</th><th style="text-align: right;">Type</th><th></th></tr></thead><tbody><tr class="odd"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/lang/Runnable.html"><code>Runnable</code></a></td><td style="text-align: right;"></td><td>→</td></tr><tr class="even"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/function/BiConsumer.html"><code>BiConsumer&lt;T, U&gt;</code></a></td><td style="text-align: right;"><code>T</code>, <code>U</code></td><td>→</td></tr><tr class="odd"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/function/BiFunction.html"><code>BiFunction&lt;T, U, R&gt;</code></a></td><td style="text-align: right;"><code>T</code>, <code>U</code></td><td>→ <code>R</code></td></tr><tr class="even"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/function/BinaryOperator.html"><code>BinaryOperator&lt;T&gt;</code></a></td><td style="text-align: right;"><code>T</code>, <code>T</code></td><td>→ <code>T</code></td></tr><tr class="odd"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/function/BiPredicate.html"><code>BiPredicate&lt;T, U&gt;</code></a></td><td style="text-align: right;"><code>T</code>, <code>U</code></td><td>→ <code class="keyword">boolean</code></td></tr><tr class="even"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/function/BooleanSupplier.html"><code>BooleanSupplier</code></a></td><td style="text-align: right;"></td><td>→ <code class="keyword">boolean</code></td></tr><tr class="odd"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/concurrent/Callable.html"><code>Callable&lt;V&gt;</code></a></td><td style="text-align: right;"></td><td>→ <code>V</code></td></tr><tr class="even"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/function/Consumer.html"><code>Consumer&lt;T&gt;</code></a></td><td style="text-align: right;"><code>T</code></td><td>→</td></tr><tr class="odd"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/function/DoubleBinaryOperator.html"><code>DoubleBinaryOperator</code></a></td><td style="text-align: right;"><code class="keyword">double</code>, <code class="keyword">double</code></td><td>→ <code class="keyword">double</code></td></tr><tr class="even"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/function/DoubleConsumer.html"><code>DoubleConsumer</code></a></td><td style="text-align: right;"><code class="keyword">double</code></td><td>→</td></tr><tr class="odd"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/function/DoubleFunction.html"><code>DoubleFunction&lt;R&gt;</code></a></td><td style="text-align: right;"><code class="keyword">double</code></td><td>→ <code>R</code></td></tr><tr class="even"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/function/DoublePredicate.html"><code>DoublePredicate</code></a></td><td style="text-align: right;"><code class="keyword">double</code></td><td>→ <code class="keyword">boolean</code></td></tr><tr class="odd"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/function/DoubleSupplier.html"><code>DoubleSupplier</code></a></td><td style="text-align: right;"></td><td>→ <code class="keyword">double</code></td></tr><tr class="even"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/function/DoubleToIntFunction.html"><code>DoubleToIntFunction</code></a></td><td style="text-align: right;"><code class="keyword">double</code></td><td>→ <code class="keyword">int</code></td></tr><tr class="odd"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/function/DoubleToLongFunction.html"><code>DoubleToLongFunction</code></a></td><td style="text-align: right;"><code class="keyword">double</code></td><td>→ <code class="keyword">long</code></td></tr><tr class="even"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/function/DoubleUnaryOperator.html"><code>DoubleUnaryOperator</code></a></td><td style="text-align: right;"><code class="keyword">double</code></td><td>→ <code class="keyword">double</code></td></tr><tr class="odd"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/function/Function.html"><code>Function&lt;T, R&gt;</code></a></td><td style="text-align: right;"><code>T</code></td><td>→ <code>R</code></td></tr><tr class="even"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/function/IntBinaryOperator.html"><code>IntBinaryOperator</code></a></td><td style="text-align: right;"><code class="keyword">int</code>, <code class="keyword">int</code></td><td>→ <code class="keyword">int</code></td></tr><tr class="odd"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/function/IntConsumer.html"><code>IntConsumer</code></a></td><td style="text-align: right;"><code class="keyword">int</code></td><td>→</td></tr><tr class="even"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/function/IntFunction.html"><code>IntFunction&lt;R&gt;</code></a></td><td style="text-align: right;"><code class="keyword">int</code></td><td>→ <code>R</code></td></tr><tr class="odd"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/function/IntPredicate.html"><code>IntPredicate</code></a></td><td style="text-align: right;"><code class="keyword">int</code></td><td>→ <code class="keyword">boolean</code></td></tr><tr class="even"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/function/IntSupplier.html"><code>IntSupplier</code></a></td><td style="text-align: right;"></td><td>→ <code class="keyword">int</code></td></tr><tr class="odd"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/function/IntToDoubleFunction.html"><code>IntToDoubleFunction</code></a></td><td style="text-align: right;"><code class="keyword">int</code></td><td>→ <code class="keyword">double</code></td></tr><tr class="even"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/function/IntToLongFunction.html"><code>IntToLongFunction</code></a></td><td style="text-align: right;"><code class="keyword">int</code></td><td>→ <code class="keyword">long</code></td></tr><tr class="odd"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/function/IntUnaryOperator.html"><code>IntUnaryOperator</code></a></td><td style="text-align: right;"><code class="keyword">int</code></td><td>→ <code class="keyword">int</code></td></tr><tr class="even"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/function/LongBinaryOperator.html"><code>LongBinaryOperator</code></a></td><td style="text-align: right;"><code class="keyword">long</code>, <code class="keyword">long</code></td><td>→ <code class="keyword">long</code></td></tr><tr class="odd"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/function/LongConsumer.html"><code>LongConsumer</code></a></td><td style="text-align: right;"><code class="keyword">long</code></td><td>→</td></tr><tr class="even"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/function/LongFunction.html"><code>LongFunction&lt;R&gt;</code></a></td><td style="text-align: right;"><code class="keyword">long</code></td><td>→ <code>R</code></td></tr><tr class="odd"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/function/LongPredicate.html"><code>LongPredicate</code></a></td><td style="text-align: right;"><code class="keyword">long</code></td><td>→ <code class="keyword">boolean</code></td></tr><tr class="even"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/function/LongSupplier.html"><code>LongSupplier</code></a></td><td style="text-align: right;"></td><td>→ <code class="keyword">long</code></td></tr><tr class="odd"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/function/LongToDoubleFunction.html"><code>LongToDoubleFunction</code></a></td><td style="text-align: right;"><code class="keyword">long</code></td><td>→ <code class="keyword">double</code></td></tr><tr class="even"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/function/LongToIntFunction.html"><code>LongToIntFunction</code></a></td><td style="text-align: right;"><code class="keyword">long</code></td><td>→ <code class="keyword">int</code></td></tr><tr class="odd"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/function/LongUnaryOperator.html"><code>LongUnaryOperator</code></a></td><td style="text-align: right;"><code class="keyword">long</code></td><td>→ <code class="keyword">long</code></td></tr><tr class="even"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/function/ObjDoubleConsumer.html"><code>ObjDoubleConsumer&lt;T&gt;</code></a></td><td style="text-align: right;"><code>T</code>, <code class="keyword">double</code></td><td>→</td></tr><tr class="odd"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/function/ObjIntConsumer.html"><code>ObjIntConsumer&lt;T&gt;</code></a></td><td style="text-align: right;"><code>T</code>, <code class="keyword">int</code></td><td>→</td></tr><tr class="even"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/function/ObjLongConsumer.html"><code>ObjLongConsumer&lt;T&gt;</code></a></td><td style="text-align: right;"><code>T</code>, <code class="keyword">long</code></td><td>→</td></tr><tr class="odd"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/function/Predicate.html"><code>Predicate&lt;T&gt;</code></a></td><td style="text-align: right;"><code>T</code></td><td>→ <code class="keyword">boolean</code></td></tr><tr class="even"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/function/Supplier.html"><code>Supplier&lt;T&gt;</code></a></td><td style="text-align: right;"></td><td>→ <code>T</code></td></tr><tr class="odd"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/function/ToDoubleBiFunction.html"><code>ToDoubleBiFunction&lt;T, U&gt;</code></a></td><td style="text-align: right;"><code>T</code>, <code>U</code></td><td>→ <code class="keyword">double</code></td></tr><tr class="even"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/function/ToDoubleFunction.html"><code>ToDoubleFunction&lt;T&gt;</code></a></td><td style="text-align: right;"><code>T</code></td><td>→ <code class="keyword">double</code></td></tr><tr class="odd"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/function/ToIntBiFunction.html"><code>ToIntBiFunction&lt;T, U&gt;</code></a></td><td style="text-align: right;"><code>T</code>, <code>U</code></td><td>→ <code class="keyword">int</code></td></tr><tr class="even"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/function/ToIntFunction.html"><code>ToIntFunction&lt;T&gt;</code></a></td><td style="text-align: right;"><code>T</code></td><td>→ <code class="keyword">int</code></td></tr><tr class="odd"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/function/ToLongBiFunction.html"><code>ToLongBiFunction&lt;T, U&gt;</code></a></td><td style="text-align: right;"><code>T</code>, <code>U</code></td><td>→ <code class="keyword">long</code></td></tr><tr class="even"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/function/ToLongFunction.html"><code>ToLongFunction&lt;T&gt;</code></a></td><td style="text-align: right;"><code>T</code></td><td>→ <code class="keyword">long</code></td></tr><tr class="odd"><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/function/UnaryOperator.html"><code>UnaryOperator&lt;T&gt;</code></a></td><td style="text-align: right;"><code>T</code></td><td>→ <code>T</code></td></tr></tbody></table>

## Custom Functional Interfaces

Declared like:

    @FunctionalInterface
    interface MyInterface {
        String method(String str);
    }

Used like:

    MyInterface doubler = str -> str + str;
    String abab = doubler.method("ab");

- Functional interface: Any interface with a single abstract method
- Can have additional `default` methods
- The [`@FunctionalInterface`](https://docs.oracle.com/javase/8/docs/api/java/lang/FunctionalInterface.html) annotation (which is optional) causes the compiler to complain if the interface is not a functional interface

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
