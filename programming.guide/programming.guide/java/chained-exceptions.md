<span class="underline"></span>

<span class="underline"></span>

Java Exceptions
---------------

1.  [Throw, Try and Catch](exceptions-throw-try-catch.html)
2.  [Java Exception Types](exception-types.html)
3.  Chained Exceptions
4.  [Custom Exception](custom-exception.html)
5.  [Difference between Checked and Unchecked Exceptions](difference-between-checked-and-unchecked-exceptions.html)
6.  [Choosing between Checked and Unchecked Exceptions](choosing-between-checked-and-unchecked-exceptions.html)
7.  [Checked Exceptions: Good or Bad?](checked-exceptions-good-or-bad.html)
8.  [Return Values vs Exceptions](return-values-vs-exceptions.html)
9.  [try + finally](try-finally.html)
10. [try-with-resources](try-with-resources.html)
11. [Stack Traces](stack-trace.html)
12. [Suppressed Exceptions](suppressed-exceptions.html)
13. [throw vs throws vs Throwable](throw-vs-throws-vs-throwable.html)
14. [List of Java Exceptions](list-of-java-exceptions.html)

Exception Related Keywords
--------------------------

1.  [throw](throw.html)
2.  [throws](throws.html)
3.  [catch](catch.html)
4.  [try](try.html)
5.  [finally](finally.html)

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

Java: Chained Exceptions
========================

Here's an example of exception *chaining* or *wrapping*:

    public Person getPerson(long id) {
        try {
            return db.selectPerson(id);
        } catch (SQLException e) {
            throw new InternalServerErrorExceptionThe SQLException is given as cause
    for the InternalServerErrorException(e);
        }
    }

The above example the `SQLException` is **the cause** for the `InternalServerErrorException`.

The `InternalServerErrorException` "wrapps" the `SQLException`.

This makes sure that the service level API doesn't throw database level exceptions. In other words, the exceptions thrown are on the right **level of abstraction** which makes the API easier to work with.

Stack Traces
------------

Causes are shown in stack traces. A stack trace of chained exceptions looks like follows:

    Exception in thread "main" example.BusinessLevelException: Business level error
            at example.BusinessLevelAPI.businessLevelMethod(BusinessLevelAPI.java:8)
            at example.ExChainExample.main(ExChainExample.java:8)
    Caused by: example.ServiceException: Service level error
            at example.Service.serviceMethod(Service.java:8)
            at example.BusinessLevelAPI.businessLevelMethod(BusinessLevelAPI.java:6)
            ... 1 more
    Caused by: example.DatabaseException: Database level error
            at example.Database.databaseMethod(Database.java:5)
            at example.Service.serviceMethod(Service.java:6)
            ... 2 more

Chained exceptions should not be confused with [*suppressed exceptions*](suppressed-exceptions.html).

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
