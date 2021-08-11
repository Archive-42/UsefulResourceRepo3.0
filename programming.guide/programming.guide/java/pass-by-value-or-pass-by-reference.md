



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

# Does Java use Pass-by-Value or Pass-by-Reference?

**TL;DR:** Java is always pass-by-value. Objects are never passed around, only references to objects, and these are passed by value, just like primitives.

When you create an object all you get is a reference to it. There's no way to "pull the thread" and get hold of the actual object it points at. Since you can't get hold of objects, you can't pass them around! That's right, you can never pass an object as argument to a method! When people (sloppily) say that an object is passed to a method, what they mean is that _a reference pointing at an object_ is passed to the method.

**Key fact 1:**  
Objects aren't passed around at all.

Primitive values and references on the other hand _are_ passed around, and both are treated the same way. If you call `method(x)` it behaves precisely the same regardless if `x` is of primitive type or of reference type: The content of `x` (whether it's an integer, a boolean value or a reference to an object) is copied and passed as argument to the method.

In programming lingo, "passing a copy of the content of a variable" is called _pass by value_.

**Key fact 2:**  
Primitives and references are passed by value.

So, if someone says to you _"Objects are passed by reference"_ (which is indeed a common misconception), you should reply with, _"No, objects aren't passed around at all. **References** are passed around, and they are passed around **by value**."_

If they continue to argue with you, just say you learned it first hand from someone with a PhD in theoretical computer science that have spent three years at Oracle developing the Java compiler.

That being said, there's an important final point to be made. When a reference is passed to a method, only the reference is copied, _not the object_. In other words, you'll have two references pointing at the same object. If you for instance have the following method…

    void someMethod(Person x) {
        x.name = "Andreas";
    }

…and do…

    Person p = new Person();
    p.name = "John";
    someMethod(p);
    System.out.println(p.name);

…it will print `Andreas`. If this surprises you, recall that `p` contains a reference to the `Person` object, and that when you call `someMethod(p)` this reference is passed on, and when the method uses it, it still points at the original object.

**Key fact 3:**  
If a method modifies an object, the modification is visible outside that method.

## A Litmus Test for Call-by-Reference

A language supports call-by-reference if (and only if) it is possible to write a `swap` method with the following functionality:

    x = 0
    y = 1
    swap(x, y)
    print(x)   // should print 1
    print(y)   // should print 0

In Java this is not possible. In C++ however, it is:

    #include <iostream>
    using namespace std;

    void swap(int& a, int& b)
    {
      int tmp = a;
      a = b;
      b = tmp;
    }

    int main(void)
    {
      int x = 0, y = 1;
      swap(x, y);
      cout << x << endl; // 1
      cout << y << endl; // 0
    }

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
