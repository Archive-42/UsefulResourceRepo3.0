<span class="underline"></span>

<span class="underline"></span>

References
----------

[Hopscotch Hashing](http://mcg.cs.tau.ac.il/papers/disc2008-hopscotch.pdf) (pdf)  
<span style="color: grey; font-style: italic; font-size: smaller">by Maurice Herlihy, Nir Shavit, Moran Tzafrir</span>

Hash Tables
-----------

1.  [Hash Tables](hash-tables.html)
2.  [Complexity](hash-tables-complexity.html)
3.  [Hash Table Load Factor and Capacity](hash-table-load-factor-and-capacity.html)
4.  [Hash Table vs Hash Set](hash-table-vs-hash-set.html)
5.  [Open vs Closed Addressing](hash-tables-open-vs-closed-addressing.html)
6.  [Open Addressing](hash-tables-open-addressing.html)
7.  [Coalesced Hashing](coalesced-hashing.html)
8.  [Cuckoo Hashing](cuckoo-hashing.html)
9.  [Robin Hood Hashing](robin-hood-hashing.html)
10. Hopscotch Hashing
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

Hopscotch Hashing
=================

A Hopscotch hash table is based on [open addressing](hash-tables-open-addressing.html) i.e. it has an array of buckets and stores at most one key-value pair in each bucket.

Upon collisions, Hopscotch hashing aims to keep key-value pairs close to the original bucket (in it's neighborhood). This keeps the chains short and achieves good memory locality.

Neighborhoods
-------------

The neighborhood of bucket *i* are the *H* consecutive buckets starting in *i*. *H* is a configurable constant.

i : i  + 1: i  + 2: i  + 3: Neighborhood of bucket i , with H  = 4.

A key-value pair will **always be stored within the neighborhood of the bucket it originally hashes to**. (During lookup, only the buckets in the relevant neighborhood are considered.)

### Neighborhoods Overlap

The neighborhoods of consecutive buckets overlap. Each bucket is part of *H* neighborhoods.

? i : j : k : l : hoods of i , j , k and l . Bucket l is part of the neighbor-

**Optimal value for *H*:** The hash table can't handle more than *H* collisions in one bucket, so *H* shouldn't be too small. Also, if *H* is too large, lookups will be less efficient. In practice, a good choice for *H* is one that optimizes the usage of the cache lines. Good performance can be achieved if an entire neighborhood can be fetched in one memory roundtrip. The implementation in the original paper uses <span class="no-wrap">*H* = 32</span>.

Insertion
---------

Suppose a key, *k*, is to be inserted, and that it hashes to bucket *i*. Bucket *i* is referred to as the **home bucket** of *k*.

### Case: Home bucket is empty

If the home bucket is empty, the key is placed there and we're done.

**Note:** Any bucket in the neighborhood of *i* is a valid bucket for *k*.

If bucket <span class="no-wrap">*i* + *d*</span> is empty, and <span class="no-wrap">*d* &lt; *H*</span>, then *k* can, if needed later, be moved down to <span class="no-wrap">*i* + *d*</span>, effectively **moving the empty space upwards**.

i : k k could be moved down Empty space would then move up

### Case: Home bucket is occupied

If bucket *i* is not empty, then we search for an empty bucket linearly, starting from *i* (linear probing). Suppose we find an empty bucket at index *j*.

If *j* is within in the neighborhood of *i* we put *k* there and return.

If *j* is outside of *i*’s neighborhood, we try to move an element between *i* and *j* downwards so that the empty space moves upwards, closer to *i*. We repeat this process until the empty space has been moved into the neighborhood of *i*, and then use that space for *k*.

For the sake of this example, let's assume that <span class="no-wrap">*i* = 17</span> and <span class="no-wrap">*j* = 24</span> and that we have neighborhoods of size 4. The home bucket of each key will be noted below the key.

16: i = 17: a 17 18: b 16 19: c 18 20: d 19 21: e 21 22: f 21 23: g 23 j = 24: 25: Home bucket for key to be inserted First empty bucket

The key to move down to *j* must have *j* in the neighborhood of its home bucket. Since no “leap” can be longer than <span class="no-wrap">*H* − 1</span> we first examine the key in bucket <span class="no-wrap">24 − (*H* − 1) = 21</span> (key *e*). We see that 21 is the home bucket of *e*. This means that *j* is within its neighborhood so we perform the swap.

16: i = 17: a 17 18: b 16 19: c 18 20: d 19 21: 22: f 21 23: g 23 j = 24: e 21 25: e is moved down to bucket 24 Empty space is now in bucket 21.

The empty space (21) is still not within the neighborhood of *i* (17-20), so we repeat.

Looking at bucket 18 (key *b*) we see that its home bucket is 16. Moving it down to the empty space at index 21 would move it out of its neighborhood, so we let it be and look at the next bucket: bucket 19 (key *c*). The home bucket of *c* is 18, which means that 22 is within its neighborhood and it's safe to swap.

16: i = 17: a 17 18: b 16 19: 20: d 19 21: c 18 22: f 21 23: g 23 j = 24: e 21 25: c is moved down to bucket 21 Empty space is now in bucket 19.

The empty space is now within the neighborhood of *i*. We use this space to insert the new key *k*. In summary, the full insertion looks as follows:

16: i = 17: a 17 18: b 16 19: c 18 20: d 19 21: e 21 22: f 21 23: g 23 j = 24: 25:

Initial state

a 17 b 16 c 18 d 19 f 21 g 23 e 21

<span class="variable">e</span> is moved to bucket 24

a 17 b 16 c 18 d 19 f 21 g 23 e 21

<span class="variable">b</span> can't be moved to bucket 21

a 17 b 16 d 19 c 18 f 21 g 23 e 21

<span class="variable">c</span> is moved to bucket 21

a 17 b 16 k 17 d 19 c 18 f 21 g 23 e 21

<span class="variable">k</span> is inserted in bucket 19

If this displacement algorithm fails (some part of the array doesn't have any swaps available) then rehashing kicks in.

### Complexity

As with other types of hash tables, worst-case complexity is *O*(*n*). However, assuming the hash function disperses the keys evenly, the **expected time complexity** is constant. See Lemma 6 in the [original paper](http://mcg.cs.tau.ac.il/papers/disc2008-hopscotch.pdf).

Lookup
------

To look up a key, *k*, the home bucket, *b*, is located based on the hash of *k*. If the home bucket stores *k* we're done, otherwise we examine the other buckets in the neighborhood that has *b* as their home bucket.

### Complexity

Since lookup examines at most *H* buckets (which is constant), lookup has a worst-case complexity of *O*(1).

Removal
-------

The relevant bucket is located the same way as a lookup is performed. The key is removed by clearing the bucket. Any meta info about neighboring buckets (discussed further down) must be updated as well.

Hopscotch hashing does not require a special “deleted” marking as other open addressing techniques do, and does not suffer from problems with contamination. (See section on contamination in [Hash Tables: Open vs Closed Addressing](hash-tables-open-vs-closed-addressing.html).)

### Complexity

Similar to the analysis of lookup; *O*(1).

Rehashing
---------

Rehashing works “as usual”. A larger array is allocated, each element is removed from the original array and inserted in the new array.

Keeping track of home buckets
-----------------------------

To quickly find suitable candidates for swapping during insert, the implementation provided in the original paper on Hopscotch hashing stores meta information about each neighborhood in the home bucket. Two variants are suggested:

-   Each bucket has a **bitmap** of *H* bits. Bit *d* in the bitmap of bucket *b* is set if and only if bucket <span class="no-wrap">*b* + *d*</span> is occupied by a key that has *b* as its home bucket.

    The benefit of this representation is that the bucket itself stores information about all keys that belong to that bucket. This is useful for lookups and for finding keys eligible for swapping.

-   In the other solution, each bucket has a **linked list** of references to other buckets. The linked list in bucket *b* contains references to all buckets storing keys that have *b* as their home bucket.

    With large neighborhoods this may be a more memory efficient representation. On the other hand it introduces some indirection which could impact performance.

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](terms-and-conditions.html)
