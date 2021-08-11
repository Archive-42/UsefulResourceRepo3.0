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

Java: Creating a custom event
=============================

Here's an example of how create your own events and listen to them. It's called the *observer pattern*. In this example the initiator prints "Hello" and the `HelloListener` responds with "Hello there!".

    // An interface to be implemented by everyone
    // interested in "Hello" events
    interface HelloListener {
        void someoneSaidHello();
    }

    // Someone who says "Hello"
    class Initiater {
        private List<HelloListener> listeners = new ArrayList<HelloListener>();

        public void addListener(HelloListener toAdd) {
            listeners.add(toAdd);
        }

        public void sayHello() {
            System.out.println("Hello!");
        
            // Notify everybody that may be interested.
            for (HelloListener hl : listeners)
                hl.someoneSaidHello();
        }
    }

    // Someone interested in "Hello" events
    class Responder implements HelloListener {
        @Override
        public void someoneSaidHello() {
            System.out.println("Hello there!");
        }
    }

And here's a little example runner:

    class Test {
        public static void main(String[] args) {
            Initiater initiater = new Initiater();
            Responder responder = new Responder();
            initiater.addListener(responder);
            initiater.sayHello();  // "Hello!" and "Hello there!"
        }
    }

Comments (2)
------------

![User avatar](https://www.gravatar.com/avatar/c0a10775d511931378e3c678b107e96d?d=mp)

Than you for this example. It works perfectly!

<span style="color: grey">by MrJW | </span> <span class="reply-button">Reply</span>

![User avatar](https://www.gravatar.com/avatar/74327a9f732282ff7aca5af7ca596d33?d=mp)

Good! Simple and clear!

<span style="color: grey">by wibrst | </span> <span class="reply-button">Reply</span>

### Add comment

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
