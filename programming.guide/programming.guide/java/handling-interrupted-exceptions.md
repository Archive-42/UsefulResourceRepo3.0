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
4.  Handling InterruptedException
5.  [Why wait must be called in a synchronized block](why-wait-must-be-in-synchronized.html)

[**See all 190 Java articles**](index.html)

Top Algorithm Articles
----------------------

1.  [Dynamic programming vs memoization vs tabulation](../dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](../big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](../sliding-window-example.html)
4.  [What makes a good loop invariant?](../what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](../random-point-within-circle.html)

Java: Handling InterruptedException
===================================

You probably come because you've called a method that throws `InterruptedException` and need to deal with it somehow.

First of all, you should see `throws InterruptedException` for what it is: A part of the method signature and a possible outcome of calling the method you're calling. So start by embracing the fact that an `InterruptedException` is a perfectly valid result of the method call.

Now, if the method you're calling throws such exception, what should *your* method do? You can figure out the answer by thinking about the following:

**Does it make sense for the method *you* are implementing to throw an `InterruptedException`?** Put differently, is an `InterruptedException` a sensible outcome when calling *your* method?

-   If **yes**, then `throws InterruptedException` should be part of *your* method signature, and you should let the exception propagate (i.e. don't catch it at all).
    **Example:** Your method waits for a value from the network to finish the computation and return a result. If the blocking network call throws an `InterruptedException` your method can not finish computation in a normal way. You let the `InterruptedException` propagate.

        int computeSum(Server server) throws InterruptedException {
            // Any InterruptedException thrown below is propagated
            int a = server.getValueA();
            int b = server.getValueB();
            return a + b;
        }

-   If **no**, then you should not declare your method with `throws InterruptedException` and you should (must!) catch the exception. Now two things are important to keep in mind in this situation:

    1.  Someone interrupted your thread. That someone is probably eager to cancel the operation, terminate the program gracefully, or whatever. You should be polite to that someone and return from your method without further ado.
    2.  Even though *your* method can manage to produce a sensible return value in case of an `InterruptedException` the fact that the thread has been interrupted may still be of importance. In particular, the code that calls your method may be interested in whether an interruption occurred during execution of your method. You should therefor log the fact an interruption took place by setting the interrupted flag: `Thread.currentThread().interrupt()`

    **Example:** The user has asked to print the sum of two values. Printing *"Failed to compute sum"* is acceptable if the sum can't be computed (and much better than letting the program crash with a stack trace due to an `InterruptedException`). In other words, it does *not* make sense to declare this method with `throws InterruptedException`.

        void printSum(Server server) {
            try {
                int sum = computeSum(server);
                System.out.println("Sum: " + sum);
            } catch (InterruptedException e) {
                Thread.currentThread().interrupt();  // set interrupt flag
                System.out.println("Failed to compute sum");
            }
        }

By now it should be clear that just doing `throw new RuntimeException(e)` is a bad idea. It isn't very polite to the caller. You could invent a new runtime exception but the root cause (someone wants the thread to stop execution) might get lost.

Another example: Implementing `Runnable`
----------------------------------------

As you may have discovered, the signature of [`Runnable.run`](https://docs.oracle.com/javase/8/docs/api/java/lang/Runnable.html#run--) does not allow for rethrowing `InterruptedExceptions`. Well, *you* signed up on implementing `Runnable`, which means that *you* signed up to deal with possible `InterruptedExceptions`. Either choose a different interface, such as [`Callable`](https://docs.oracle.com/javase/8/docs/api/java/util/concurrent/Callable.html), or follow the second approach above.

Yet another: Calling `Thread.sleep`
-----------------------------------

You're attempting to read a file and the spec says you should try 10 times with 1 second in between. You call `Thread.sleep(1000)`. So, you need to deal with `InterruptedException`. For a method such as `tryToReadFile` it makes perfect sense to say, *"If I'm interrupted, I can't complete my action of trying to read the file"*. In other words, it makes perfect sense for the method to throw `InterruptedExceptions`.

    String tryToReadFile(File f) throws InterruptedException {
        for (int i = 0; i < 10; i++) {
            if (f.exists())
                return readFile(f);
            Thread.sleep(1000);
        }
        return null;
    }

Comments (4)
------------

![User avatar](https://www.gravatar.com/avatar/d41d8cd98f00b204e9800998ecf8427e?d=mp)

I've gone through a bunch of articles on handling `InterruptedException` and have not found any example which says that an operation should be retried upon `InterruptedException`. So I assumed all authors, including you, implied that this exception should not be retried.

Is this the case? Does `InterruptedException` imply cancel/terminate, or can it also imply something else, like retry?

<span style="color: grey">by Abhishek Agrawal | </span> <span class="reply-button">Reply</span>

![User avatar](https://www.gravatar.com/avatar/99e100243aaa8b1469b1ed4e8bbecb06?d=mp)

An interrupt means that someone wants the thread to bail out from its currently blocking operation. It's indeed common that this is part of some higher level "abort", like user tries to terminate the application, but this is arguably not always the case.

Ultimately it is only the thread that interrupts that knows the reason for the interruption, so generally speaking the interrupting thread needs to communicate the intention to the interrupted thread, unless it's implicitly clear from the context. For example, if someone pokes at me while I'm reading a book, and I look up at him, I expect him to tell me what he wants. If he gives me a blank stare, (and it's not clear from the context) then I will not know how to respond to the interruption.

<span style="color: grey">by Andreas Lundblad | </span> <span class="reply-button">Reply</span>

![User avatar](https://www.gravatar.com/avatar/d41d8cd98f00b204e9800998ecf8427e?d=mp)

How would the interrupting thread communicate why it is interrupting another thread?

<span style="color: grey">by Kevin Garrett | </span> <span class="reply-button">Reply</span>

![User avatar](https://www.gravatar.com/avatar/99e100243aaa8b1469b1ed4e8bbecb06?d=mp)

Threads can communicate with each other by for instance sharing a reference to a synchronized message queue, such as an `ArrayBlockingQueue`. The interrupting thread could then do `msgQueue.offer("timeout")` and the interrupted thread could do `msgQueue.take()` to retrieve the message.

<span style="color: grey">by Andreas Lundblad | </span> <span class="reply-button">Reply</span>

### Add comment

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
