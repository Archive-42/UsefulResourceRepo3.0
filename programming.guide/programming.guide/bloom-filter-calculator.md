



## Top Algorithm Articles

1.  [Dynamic programming vs memoization vs tabulation](dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](sliding-window-example.html)
4.  [What makes a good loop invariant?](what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](random-point-within-circle.html)

[**See all algorithm articles**](algorithms.html)



## Top Java Articles

1.  [Do interfaces inherit from Object?](java/do-interfaces-inherit-from-object.html)
2.  [Executing code in comments?!](java/executing-code-in-comments.html)
3.  [Functional Interfaces](java/functional-interfaces.html)
4.  [Handling InterruptedException](java/handling-interrupted-exceptions.html)
5.  [Why wait must be called in a synchronized block](java/why-wait-must-be-in-synchronized.html)

[**See all Java articles**](java/index.html)

# Bloom Filter Calculator

Here's an interactive tool to help you tune the parameters for a Bloom filter. If you want to learn more about how Bloom filters work, see separate article [here](bloom-filter.html).

**Number of bits (_m_)**

*m* = <span id="m-bits"></span>

In bytes: <span id="m-bytes"></span>

**Number of hash functions (_k_)**

*k* = <span id="k-lbl"></span>

This in the optimal choice for <span class="no-wrap">*n* = <span id="k-opt-for-n"></span></span>

Not the optimal choice for any number of elements.

**Acceptable false positive rate (_p_)**

*p* = <span id="p-percent"></span> %

Allows for up to <span id="n-max"></span> elements.

Allows no elements to be added.

1 0 p n 1 2 3 4 5 6 7 8 9

## Probability of false positives

Assuming uniform and independent hashing, the probability of a specific bit not being set to 1 after a single use of a hash function is

1

−

1

_m_

After inserting _n_ elements using _k_ hashes each, the probability of a specific bit still being 0 is thus

⎛  
⎝

1

−

1

_m_

⎞  
⎠

_kn_

Conversely, the probability of a specific bit being set to 1, is

1

−

⎛  
⎝

1

−

1

_m_

⎞  
⎠

_kn_

Since a false positive requires _k_ random bits to be set to 1, the probability of a false positive after inserting _n_ elements is

⎛  
⎝

1

−

⎛  
⎝

1

−

1

_m_

⎞  
⎠

_kn_

⎞  
⎠

_k_

Using the formula for calculating _e_…

_e_

=

lim

*x* → ∞

⎛  
⎝

1

−

1

_x_

⎞  
⎠

−*x*

…we can approximate the probability of false positives as

(

1 − *e*

−*kn* / *m*

)

_k_

## Optimal value for k

By fixing the *n* / *m* ratio in the previous equation, we can solve for _k_, and find the optimal value for it. That is, if you for example know you can spare 1 MB for the bit vector, and you know that you will insert ~10,000 elements, you can calculate the number of hash functions that **minimizes the false positives** in subsequent lookups.

Given _n_ and _m_ we want to minimize

=

(

1 − *e*

−*kn* / *m*

)

_k_

=

_e_

ln

(

1 − *e*

−*kn* / *m*

)

_k_

=

_e_

_k_

ln

(

1 − *e*

−*kn* / *m*

)

In other words, we want to minimize

_k_

ln

(

1 − *e*

−*kn* / *m*

)

By simple rules of powers and logarithms, we know that <span class="no-wrap">k = −*m* / *n* ln(e<sup>−*kn* / *m*</sup>)</span>, so we can rewrite the above as follows:

−

_m_

_n_

ln

(

_e_

−*kn* / *m*

)

ln

(

1 − *e*

−*kn* / *m*

)

By symmetry, we see that this is minimized when <span class="no-wrap">e<sup>−*kn* / *m*</sup> = 1 − e<sup>−*kn* / *m*</sup></span>, i.e. when <span class="no-wrap">e<sup>−*kn* / *m*</sup> = 0.5</span>. Intuitively this means that we should chose a _k_ such that after insterting _n_ elements, half of the _m_ bits are set to true. Solving for _k_ gives us

_k_

=

*m* ln 2

_n_

With this value for _k_ the optimal false positive rate is approximately 0.6185<sup>*m* / *n*</sup>.

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](terms-and-conditions.html)
