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
5.  Why wait must be called in a synchronized block

[**See all 190 Java articles**](index.html)

Top Algorithm Articles
----------------------

1.  [Dynamic programming vs memoization vs tabulation](../dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](../big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](../sliding-window-example.html)
4.  [What makes a good loop invariant?](../what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](../random-point-within-circle.html)

Java: Why wait must be called in a synchronized block
=====================================================

Let's look at an example of what issues we would run into if `wait()` could be called outside of a synchronized block.

Suppose we were to implement a blocking queue.

A first attempt (without synchronization) could look something along the lines below

    class BlockingQueue {
        Queue<String> buffer = new LinkedList<String>();
        
        public void give(String data) {
            buffer.add(data);
            notify();  // Since someone may be waiting in take
        }
        
        public String take() throws InterruptedException {
            while (buffer.isEmpty())  // Avoid "if" due to spurious wakeups
                wait();
            return buffer.remove();
        }
    }

This is what could potentially happen:

1.  A consumer thread calls `take()` and sees that the `buffer.isEmpty()`.

2.  Before the consumer thread goes on to call `wait()`, a producer thread comes along and invokes a full `give()`, that is, `buffer.add(data); notify();`

3.  The consumer thread will now call `wait()` (and *miss* the `notify()` that was just called).

4.  If unlucky, there will be no more calls to `give` and the consumer is stuck in `wait` indefinitely, even though there's data available to be consumed.

Once you understand the issue, the solution is obvious: Use `synchronized` to make sure `notify` is never called between `isEmpty` and `wait`.

Without going into details: This synchronization issue is universal. Wait / notify always boils down to communicating something, and inter-thread communication without synchronization is almost always broken.

Put Formally
------------

[Here](http://coding.derkeiler.com/Archive/Java/comp.lang.java.programmer/2006-01/msg01130.html) is a more formal description given by Chris Smith.

> \[…\] You need an absolute guarantee that the waiter and the notifier agree about the state of the predicate. The waiter checks the state of the predicate at some point slightly BEFORE it goes to sleep, but it depends for correctness on the predicate being true WHEN it goes to sleep. There's a period of vulnerability between those two events, which can break the program. \[…\]
>
> The predicate that the producer and consumer need to agree upon is in the above example `buffer.isEmpty()`. And the agreement is resolved by ensuring that the wait and notify are performed in `synchronized` blocks.

Comments (4)
------------

![User avatar](https://www.gravatar.com/avatar/d41d8cd98f00b204e9800998ecf8427e?d=mp)

Hi, I have a question. If a consumer thread calls `take()` and go into synchronized block (assumed there is an synchronized object) then `wait()`, how would the producer thread call `give()`, which is protected by the same synchronized object? Is this another deadlock?

<span style="color: grey">by Chen Wei | </span> <span class="reply-button">Reply</span>

![User avatar](https://www.gravatar.com/avatar/99e100243aaa8b1469b1ed4e8bbecb06?d=mp)

Good question. The answer can be found in the [javadoc of the `Object.wait` method](https://docs.oracle.com/javase/9/docs/api/java/lang/Object.html#wait--):

*"\[...\] The thread releases ownership of this monitor and waits until another thread notifies threads waiting on this object's monitor to wake up either through a call to the notify method or the notifyAll method. \[...\]"*

So the producer calling `give()` is allowed in, because while inside the `Object.wait` method, the monitor is temporarily released.

<span style="color: grey">by Andreas Lundblad | </span> <span class="reply-button">Reply</span>

![User avatar](https://www.gravatar.com/avatar/d41d8cd98f00b204e9800998ecf8427e?d=mp)

Point \#4 says -

*"If unlucky, there will be no more calls to give and the consumer is stuck in wait indefinitely, even though there’s data available to be consumed."*

Any example for the unlucky situation??

<span style="color: grey">by Dinesh Ranawat | </span> <span class="reply-button">Reply</span>

![User avatar](https://www.gravatar.com/avatar/99e100243aaa8b1469b1ed4e8bbecb06?d=mp)

Here's an example of such unlucky situation:

Suppose you have an algorithm that may have at most 1 pending outstanding task at any given time. If one task gets "stuck in the queue" indefinitely because a `notify()` was missed by the consumer, then the producer can't enqueue more tasks, and the algorithm as a whole will get stuck.

<span style="color: grey">by Andreas Lundblad | </span> <span class="reply-button">Reply</span>

### Add comment

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
