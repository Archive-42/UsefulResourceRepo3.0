<span class="underline"></span>

<span class="underline"></span>

Hash Tables
-----------

1.  [Hash Tables](hash-tables.html)
2.  [Complexity](hash-tables-complexity.html)
3.  [Hash Table Load Factor and Capacity](hash-table-load-factor-and-capacity.html)
4.  [Hash Table vs Hash Set](hash-table-vs-hash-set.html)
5.  [Open vs Closed Addressing](hash-tables-open-vs-closed-addressing.html)
6.  Open Addressing
7.  [Coalesced Hashing](coalesced-hashing.html)
8.  [Cuckoo Hashing](cuckoo-hashing.html)
9.  [Robin Hood Hashing](robin-hood-hashing.html)
10. [Hopscotch Hashing](hopscotch-hashing.html)
11. [2-Choice Hashing](2-choice-hashing.html)
12. [2-Left Hashing](2-left-hashing.html)
13. [Linked Hash Table](linked-hash-table.html)
14. [Why large prime numbers are used in hash tables](prime-numbers-in-hash-tables.html)

<span class="underline"></span>

Top Algorithm Articles
----------------------

1.  [Dynamic programming vs memoization vs tabulation](dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](sliding-window-example.html)
4.  [What makes a good loop invariant?](what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](random-point-within-circle.html)

[**See all algorithm articles**](algorithms.html)

Hash Tables: Open Addressing
============================

A hash table based on **open addressing** (sometimes referred to as **closed hashing**) stores all elements directly in the hast table array, i.e. it has at most one element per bucket. The benefits of this approach are:

-   **Predictable memory usage**  
    No allocation of new nodes when keys are inserted
-   **Less memory overhead**  
    No next pointers
-   **Memory locality**  
    A linear memory layout provides better cache characteristics

☞

For brief a comparison with closed addressing, see [Open vs Closed Addressing](hash-tables-open-vs-closed-addressing.html).

Insertion
---------

When inserting a key that hashes to an already occupied bucket, i.e. a **collision** occurs, the search for an empty bucket proceeds through a predefined search sequence. The first empty bucket found is used for the new key.

**Example:** Inserting key *k* using linear probing. (Other probing techniques are described later on.)

insert( k ) hash( k ) = third bucket ? Occupied ? Occupied ? Occupied Empty, insert k here

Rehashing ensures that an empty bucket can always be found.

Lookup
------

When looking up a key, the same search sequence is used. The search terminates when the key is found, or an empty bucket is found in which case the key does not exist in the table.

**Example:** Here's how a successful lookup could look:

lookup( k ) hash( k ) = third bucket x Wrong key y Wrong key z Wrong key k Key found!

**Example:** Here's how an usuccessful lookup could look:

lookup( k ) hash( k ) = third bucket x Wrong key y Wrong key z Wrong key Empty: Key not found

Removal
-------

Since the lookup algorithm terminates if an empty bucket is found, care must be taken when removing elements. If a bucket is simply cleared out, it can create a gap in the search sequence, and cause the lookup algorithm to terminate too early.

For this reason, buckets are typically not cleared, but instead marked as "deleted". Such buckets, called **tombstones**, do not cause lookups to terminate early, and can be reused by the insert algorithm

### Contamination

As data is inserted and deleted over and over, empty buckets are gradually replaced by tombstones. As the sequences of non-empty buckets get longer, the performance of lookups degrade. This phenomenon is called **contamination**, and the only way to recover from it is to rehash.

Various Probing Techniques
--------------------------

The order in which insert and lookup scans the array varies between implementations. A few common techniques are described below. (All indexes are modulo the array length.)

### Linear Probing

If a collision occurs in bucket *i*, the search sequence continues with

-   *i* + 1
-   *i* + 2
-   *i* + 3
-   …

This approach achieves good cache performance since the probing sequence is linear in memory.

A problem however, is that it tends to create long sequences of occupied buckets. The reason is that an existing chain will act as a "net" and catch many of the new keys, which will be appended to the chain and exacerbate the problem.

**Example:** Consider the probabilities for which bucket the next key will end up in, in the following situation:

10% 10% 0% (occupied) ? 0% (occupied) ? 0% (occupied) ? 40% 10% 10% 10% 10%

In other words, long chains get longer and longer, which is bad for performance since the average number of buckets scanned during insert and lookup increases. The phenomenon is called **primary clustering** or just **clustering**.

### Quadratic Probing

With quadratic probing a search sequence starting in bucket *i* proceeds as follows:

-   *i* + 1<sup>2</sup>
-   *i* + 2<sup>2</sup>
-   *i* + 3<sup>2</sup>
-   …

This creates larger and larger gaps in the search sequence and avoids primary clustering.

If one key hashes to the same bucket as another key, the search sequence for the second key will go in the footsteps of the first one. If this happens repeatedly (for example due to a poorly implemented hash function) long chains will still form, and cause performance to degrade. The phenomenon is called **secondary clustering**.

### Double Hashing

With double hashing, another hash function, *h*<sub>2</sub> is used to determine the size of the steps in the search sequence. If <span class="no-wrap">*h*<sub>2</sub>(key) = *j*</span> the search sequence starting in bucket *i* proceeds as follows:

-   *i* + 1 × *j*
-   *i* + 2 × *j*
-   *i* + 3 × *j*

(If *j* happens to evaluate to a multiple of the array length, 1 is used instead.)

This approach is worse than the previous two regarding memory locality and cache performance, but avoids both primary and secondary clustering.

### Comparison of Probing Techniques

Linear Probing

Quadratic Probing

Double Hashing

Complexity
----------

The naive open addressing implementation described so far have the usual properties of a hash table. Insert, lookup and remove all have *O*(*n*) as worst-case complexity and *O*(1) as expected time complexity (under the simple uniform hashing assumption).

See separate article, [Hash Tables: Complexity](hash-tables-complexity.html), for details.

Variations of Open Addressing
-----------------------------

There are many, more sophisticated, techniques based on open addressing. The main objective is often to mitigate clustering, and a common theme is to move around existing keys when inserting a new key. With clever key displacement algorithms, keys can end up closer to the buckets they originally hashed to, and thus improve memory locality and overall performance.

Examples of open addressing techniques (strongly recommended reading):

-   [Coalesced Hashing](coalesced-hashing.html)
-   [Cuckoo Hashing](cuckoo-hashing.html)
-   [Robin Hood Hashing](robin-hood-hashing.html)
-   [Hopscotch Hashing](hopscotch-hashing.html)

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](terms-and-conditions.html)
