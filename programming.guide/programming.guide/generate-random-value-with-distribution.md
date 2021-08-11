<span class="underline"></span>

<span class="underline"></span>

## Top Algorithm Articles

1.  [Dynamic programming vs memoization vs tabulation](dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](sliding-window-example.html)
4.  [What makes a good loop invariant?](what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](random-point-within-circle.html)

[**See all algorithm articles**](algorithms.html)

<span class="underline"></span>

## Top Java Articles

1.  [Do interfaces inherit from Object?](java/do-interfaces-inherit-from-object.html)
2.  [Executing code in comments?!](java/executing-code-in-comments.html)
3.  [Functional Interfaces](java/functional-interfaces.html)
4.  [Handling InterruptedException](java/handling-interrupted-exceptions.html)
5.  [Why wait must be called in a synchronized block](java/why-wait-must-be-in-synchronized.html)

[**See all Java articles**](java/index.html)

# Generating a random value with a custom distribution

To generate random values according to a **custom distribution** using a function that generates **uniform random values between 0 and 1** you can use the [inverse transform sampling](https://en.wikipedia.org/wiki/Inverse_transform_sampling) method.

## Method Outline

1.  First we create a [cumulative distribution function](https://en.wikipedia.org/wiki/Cumulative_distribution_function) (CDF for short)
2.  We then mirror the CDF along _y_ = _x_
3.  The resulting function can be applied to a random value between 0 and 1

## Example

Suppose we want to generate a random point with the following distribution:

- 1/5 of the points uniformly between 1 and 2, and
- 4/5 of the points uniformly between 2 and 3.

The [probability density function](https://en.wikipedia.org/wiki/Probability_density_function) (PDF) in this case would look like this:

0 1 2 3

For such simple distribution, inverse transform sampling is a bit of an overkill, but let's go with this since a simple example makes it easier to understand the general idea.

**Step 1: Create the CDF**

The CDF is, as the name suggests, the cumulative version of the PDF. Intuitively: While PDF(_x_) describes the number of random values _at x_, CDF(_x_) describes the number of random values _less than x_.

Since we're working with reals, the CDF is expressed as the integral of the PDF. In this case the CDF would look like:

0 1 2 3 1

To see why the CDF is useful, imagine that we shoot bullets from left to right at uniformly distributed heights. As the bullets hit the line, they drop down to the ground:

0 1 2 3 1

See how the density of the bullets on the ground corresponds to our desired distribution! We're almost there!

**Step 2: Mirror the CDF along _y_ = _x_**

The problem is that for this function, the _x_ axis is the _input_ and the _y_ axis is the _output_. We can only “shoot bullets from the ground straight up”! We need the inverse function!

This is why we mirror the whole thing; _x_ becomes _y_ and _y_ becomes _x_:

0 3 3 CDF CDF⁻¹

We call this _CDF_<sup>-1</sup>.

**Step 3: Apply the resulting function to a uniform value between 0 and 1**

With the _CDF_<sup>-1</sup> we have all we need. We now simply feed it with uniformly random values between 0 and 1:

_CDF_<sup>-1</sup>(_random_())

The result is random values with the desired distribution.

## A Real World Example

This technique is used to derive the algorithm for generating a uniformly random point on a disc. See article [Generating a random point within a circle (uniformly)](random-point-within-circle.html).

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](terms-and-conditions.html)
