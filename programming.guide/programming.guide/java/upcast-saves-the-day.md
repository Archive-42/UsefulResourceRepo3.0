<span class="underline"></span>

<span class="underline"></span>

Featured Stack Overflow Post
----------------------------

[In Java, difference between default, public, protected, and private](https://stackoverflow.com/a/33627846/276052)  
  
[<img src="../images/so-featured-33627846.png" alt="StackOverflow screenshot thumbnail" class="screenshot" />](https://stackoverflow.com/a/33627846/276052)

<span class="underline"></span>

Top Java Articles
-----------------

1.  [Do interfaces inherit from Object?](do-interfaces-inherit-from-object.html)
2.  [Executing code in comments?!](executing-code-in-comments.html)
3.  [Functional Interfaces](functional-interfaces.html)
4.  [Handling InterruptedException](handling-interrupted-exceptions.html)
5.  [Why wait must be called in a synchronized block](why-wait-must-be-in-synchronized.html)

[**See all 190 Java articles**](index.html)

Top Algorithm Articles
----------------------

1.  [Dynamic programming vs memoization vs tabulation](../dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](../big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](../sliding-window-example.html)
4.  [What makes a good loop invariant?](../what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](../random-point-within-circle.html)

Java Oddity: How an upcast can save the day
===========================================

You almost never see an **upcast** in Java code. That is, you rarely see something like this:

    …((Animal) someDog)…

Why would you need to? The fact that a `Dog` is an `Animal` should be evident to the compiler!

Here is however a program that **fails to compile** without an upcast:

`class Player {`  
`    private             boolean isAlive =             true;`  
  
`    void             kill(Opponent opponent) {`  

        // Compiles

        // Error: 'isAlive' has private access in 'Player'

       

 ((Player)

 opponent

)

.<span id="isAlive">isAlive</span> = <span class="keyword">false</span>;

  

        // opponent.opponentSpecificMethod();

`    }`  
`}`  
  
`class Opponent             extends Player {                 // ...             }`

**Note:** The snippet above is written to illustrate a language oddity and should not be seen as an example of good design. In fact, the need for an upcast is a telltale of a bad design. In particular a base class should not be coupled to one of its subclasses the way `Player` is coupled to `Opponent`.

Comments (2)
------------

![User avatar](https://www.gravatar.com/avatar/e5c1d6ea2af32dbecfb13454db124189?d=mp)

Private members cannot be accessed by child classes. You want protected access.

<span style="color: grey">by holothuroid | </span> <span class="reply-button">Reply</span>

![User avatar](https://www.gravatar.com/avatar/99e100243aaa8b1469b1ed4e8bbecb06?d=mp)

No one is accessing `isAlive` from a child class here. The field is used only in `Player`, and thus anything but `private` would be an unncessary sacrifice of encapsulation.

<span style="color: grey">by Andreas Lundblad | </span> <span class="reply-button">Reply</span>

### Add comment

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
