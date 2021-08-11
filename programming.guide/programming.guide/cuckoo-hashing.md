<span class="underline"></span>

<span class="underline"></span>

## Hash Tables

1.  [Hash Tables](hash-tables.html)
2.  [Complexity](hash-tables-complexity.html)
3.  [Hash Table Load Factor and Capacity](hash-table-load-factor-and-capacity.html)
4.  [Hash Table vs Hash Set](hash-table-vs-hash-set.html)
5.  [Open vs Closed Addressing](hash-tables-open-vs-closed-addressing.html)
6.  [Open Addressing](hash-tables-open-addressing.html)
7.  [Coalesced Hashing](coalesced-hashing.html)
8.  Cuckoo Hashing
9.  [Robin Hood Hashing](robin-hood-hashing.html)
10. [Hopscotch Hashing](hopscotch-hashing.html)
11. [2-Choice Hashing](2-choice-hashing.html)
12. [2-Left Hashing](2-left-hashing.html)
13. [Linked Hash Table](linked-hash-table.html)
14. [Why large prime numbers are used in hash tables](prime-numbers-in-hash-tables.html)

## Resources

[Cuckoo Hashing](https://www.cs.tau.ac.il/~shanir/advanced-seminar-data-structures-2009/bib/pagh01cuckoo.pdf)  
<span style="color: grey; font-style: italic; font-size: smaller">by Rasmus Pagh, Flemming Friche Rodler</span>

[Cuckoo Hashing: Visualization + Explanation](https://www.youtube.com/watch?v=OBuGqu2d4v4)  
<span style="color: grey; font-style: italic; font-size: smaller">by Bridger Howell, Joe Whitney</span>

[Space Ecient Hash Tables With Worst Case Constant Access Time](http://www.itu.dk/people/pagh/papers/d-cuckoo.pdf) (d-cuckoo hashing)  
<span style="color: grey; font-style: italic; font-size: smaller">by Dimitris Fotakis, Rasmus Pagh, Peter Sanders, Paul Spirakis</span>

[More Robust Hashing: Cuckoo Hashing with a Stash](https://www.eecs.harvard.edu/~michaelm/postscripts/esa2008full.pdf)  
<span style="color: grey; font-style: italic; font-size: smaller">by Adam Kirsch, Michael Mitzenmacher, Udi Wieder</span>

[Cuckoo Hashing](https://en.wikipedia.org/wiki/Cuckoo_hashing)  
<span style="color: grey; font-style: italic; font-size: smaller">Wikipedia</span>

<span class="underline"></span>

## Top Algorithm Articles

1.  [Dynamic programming vs memoization vs tabulation](dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](sliding-window-example.html)
4.  [What makes a good loop invariant?](what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](random-point-within-circle.html)

[**See all algorithm articles**](algorithms.html)

# Cuckoo Hashing

Cuckoo Hashing is a technique for implementing a hash table. As opposed to most other hash tables, it achieves **constant time worst-case complexity for lookups**.

Collisions are handled by evicting existing keys and moving them from one array to the other. This resembles the way a cuckoo chick [pushes out an egg from the nest](https://www.youtube.com/watch?v=SO1WccH2_YM) to make room for itself, hence the name Cuckoo Hashing.

## Representation

It is implemented using **two arrays of equal size** and **two hash functions**:

**Example:** A Cuckoo Hash table with room for 16 keys.

h 1 h 2

Each hash function is associated with one of the arrays, i.e. it can be thought of as two separate sub hash tables.

It is similar to [open addressing](hash-tables-open-addressing.html) in the sense that each array slot can hold **at most one** key at a time.

## Insertion

A new element is always inserted in the first hash table. Should a collision occurr, the existing element is kicked out and inserted in the second hash table. Should that in turn cause a collision, the second existing element will be kicked out and inserted in the first hash table, and so on. This continues until an empty bucket is found.

**Example:** The key _a_ is inserted in the Cuckoo Hash table below. Keys get kicked around until a free slot is found.

h 1 h 2 a b c d e f g

If the number of displacements reaches a certain threshold (for instance due to a cycle among the inserted keys) rehashing takes place.

Rehashing is a linear operation, so **worst-case complexity is _O_(_n_)**. Just as with other hashing techniques however, **the ammortized run time can be shown to be _O_(1)**. The proof for this is non-trivial. See [the original paper](https://www.cs.tau.ac.il/~shanir/advanced-seminar-data-structures-2009/bib/pagh01cuckoo.pdf) for details.

The performance degrades significantly as the load factor surpasses 50%. Higher load factor than this is not even considered in the original paper.

## Lookup

If a key exists, it will be stored in its original bucket, either in the first array or the second one. In other words, **at most two lookups** are needed to figure out if the key exists or not, thus the **worst-case complexity is _O_(1)**.

## Removal

Removal is done simply by clearing the bucket storing the key. Again, worst-case complexity is **_O_(1)**.

As opposed to other open addressing schemes there are no chains and no need to use deleted markings or so called tombstones (cf. section on removal in [Hash Tables: Open Addressing](hash-tables-open-addressing.html))

## Stashing

There's a small probability that a cycle is formed among the first few elements inserted. This may trigger a rehash even at a low load factor. To mitigate this, a constant-sized array called the **stash** can be used.

When a key is to be inserted, and a free bucket can't be found, the key is stored in the stash instead. The lookup algorithm is modified to search in the stash in addition to the two arrays. Rehashing is performed when a key can't be inserted and the stash is full.

Even with a stash of just three or four cells, rehashing can be postponed significantly and allow the hash table to function with higher load factors. Intuitively, the stash "takes the edge off" of the worst case scenario. Conceptually this is similar to the cellar in [Coalesced Hashing](coalesced-hashing.html) and the improvements achieved by using [2-Choice Hashing](2-choice-hashing.html).

With a fixed size stash, the runtime overhead is of _O_(1) for all operations, i.e. the Big-O complexity is unaffected.

## D-Cuckoo Hashing

Cuckoo hashing can be generalized to use an arbitrary but fixed number of internal hash tables.

**Example:** A Cuckoo Hash table with 4 "layers".

h 1 h 2 h 3 h 4

Then a key in layer _i_ is evicted, it is inserted in layer <span class="no-wrap">*i* + 1</span> (mod number of layers).

As with other techniques leveraging multiple hash functions, more hash functions increases the spread and reduces the likelyhood of rehash for a given number of insertions. The improvement going from two layers to three (and beyond) is however smaller than the improvement gained when going from one to two.

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](terms-and-conditions.html)
