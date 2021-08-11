<span class="underline"></span>

<span class="underline"></span>

## In a Nutshell

<table><colgroup><col style="width: 33%" /><col style="width: 33%" /><col style="width: 33%" /></colgroup><thead><tr class="header"><th style="text-align: left;"> </th><th style="text-align: center;">Worst case</th><th style="text-align: center;">Expected case</th></tr></thead><tbody><tr class="odd"><td style="text-align: left;">Insert</td><td style="text-align: center;"><p><em>O</em>(<em>n</em>)</p></td><td style="text-align: center;"><p><em>O</em>(1)</p></td></tr><tr class="even"><td style="text-align: left;">Lookup</td><td style="text-align: center;"><p><em>O</em>(<em>n</em>)</p></td><td style="text-align: center;"><p><em>O</em>(1)</p></td></tr><tr class="odd"><td style="text-align: left;">Remove</td><td style="text-align: center;"><p><em>O</em>(<em>n</em>)</p></td><td style="text-align: center;"><p><em>O</em>(1)</p></td></tr></tbody></table>

## Hash Tables

1.  [Hash Tables](hash-tables.html)
2.  Complexity
3.  [Hash Table Load Factor and Capacity](hash-table-load-factor-and-capacity.html)
4.  [Hash Table vs Hash Set](hash-table-vs-hash-set.html)
5.  [Open vs Closed Addressing](hash-tables-open-vs-closed-addressing.html)
6.  [Open Addressing](hash-tables-open-addressing.html)
7.  [Coalesced Hashing](coalesced-hashing.html)
8.  [Cuckoo Hashing](cuckoo-hashing.html)
9.  [Robin Hood Hashing](robin-hood-hashing.html)
10. [Hopscotch Hashing](hopscotch-hashing.html)
11. [2-Choice Hashing](2-choice-hashing.html)
12. [2-Left Hashing](2-left-hashing.html)
13. [Linked Hash Table](linked-hash-table.html)
14. [Why large prime numbers are used in hash tables](prime-numbers-in-hash-tables.html)

<span class="underline"></span>

## Top Algorithm Articles

1.  [Dynamic programming vs memoization vs tabulation](dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](sliding-window-example.html)
4.  [What makes a good loop invariant?](what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](random-point-within-circle.html)

[**See all algorithm articles**](algorithms.html)

# Hash Tables: Complexity

This article is written with separate chaining and closed addressing in mind, specifically implementations based on **arrays of linked lists**. Most of the analysis however applies to other techniques, such as basic open addressing implementations.

☞

Only operations that scale with the number of elements _n_ are considered in the analysis below. In particular, the hash function is assumed to run in constant time.

## Length of chains

As is clear from the way lookup, insert and remove works, the run time is proportional to the number of keys in the given chain. So, to analyze the complexity, we need to analyze the length of the chains.

### Worst Case

If we're unlucky with the keys we encounter, or if we have a poorly implemented hash function, all keys may hash to the same bucket.

This means that the **worst-case complexity of a hash table is the same as that of a linked list**: _O_(_n_) for insert, lookup and remove.

This is however a pathological situation, and the theoretical worst-case is often uninteresting in practice. When discussing complexity for hash tables the focus is usually on **expected** run time.

### Uniform Hashing

The expected length of any given linked list depends on how the hash function spreads out the keys among the buckets. For the purpose of this analysis, we will assume that we have an ideal hash function. This is a common assumption to make. So common in fact, that it has a name:

### Simple Uniform Hashing Assumption

In a hash table with _m_ buckets, each key is hashed to any given bucket…

- …with the same probability, 1 / *m*
- …independently of which bucket any other key is hashed to.

With SUHA the keys are distributed **uniformly** and the expected length of any given linked list is therefore <span class="no-wrap">*n* / *m*</span>.

### The Magic Part

As you may recall, the <span class="no-wrap">*n* / *m*</span> ratio is called the load factor, and that rehashing guarantees that this is bound by the configured load factor limit. (See [Hash Table Load Factor and Capacity](hash-table-load-factor-and-capacity.html).) Since the load factor limit is constant, **the expected length of all chains can be considered constant**.

☞

**A common misconception** is that SUHA implies constant time worst case complexity. SUHA however, does not say that all keys _will_ be distributed uniformly, only that the probability distribution is uniform. Even with a uniform probability, it is still _possible_ for all keys to end up in the same bucket, thus worst case complexity is still linear.

## Insert

An insertion will search through one bucket linearly to see if the key already exists. This runs in <span class="no-wrap">_O_(*n* / *m*)</span> which we know from the previous section is _O_(1). If the key is found, a value is updated, if not, a new node is appended to the list. Regardless of which, this part is in _O_(1).

If we're unlucky, rehashing is required before all that. Since rehashing performs _n_ constant time insertions, it runs in Θ(_n_).

That being said, rehashes are rare. In fact, they are so rare that _in average_ insertion still runs in constant time. We say that the **amortized time complexity for insert is _O_(1)**.

**Proof:** Suppose we set out to insert _n_ elements and that rehashing occurs at each power of two. Let's assume also that _n_ is a power of two so we hit the worst case scenario and have to rehash on the very last insertion.

We would have to rehash after inserting element 1, 2, 4, …, _n_. Since each rehashing reinserts all current elements, we would do, in total, <span class="no-wrap">1 + 2 + 4 + 8 + … + _n_ = 2*n* − 1</span> extra insertions due to rehashing. In other words, all rehashing necessary incurs an average overhead of less than 2 extra insertions per element.

We conclude that despite the growing cost of rehashing, the average number of insertions per element stays constant.

## Lookup

A lookup will search through the chain of one bucket linearly. This is in <span class="no-wrap">_O_(*n* / *m*)</span> which, again, is **_O_(1)**.

## Removal

A removal will search through one bucket linearly. If the key is found, it is “unlinked” in constant time, so remove runs in **_O_(1)** as well.

If one wants to reclaim unused memory, removal may require allocating a smaller array and rehash into that. In this case removal runs in _O_(_n_) in worst case, and _O_(1) amortized.

## Traversal

There's no way to know which buckets are empty, and which ones are not, so all buckets must be traversed. This means traversal is <span class="no-wrap">Θ(_n_ + _m_)</span>.

In practice this is only relevant if the hash table is initialized with a very large capacity. After the first rehashing the number of buckets can be considered linearly proportional to the number of items, and traversal is _Θ_(_n_).

☞

One can avoid traversing the empty buckets by using an additional linked list. For details see article [Linked Hash Table](linked-hash-table.html).

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](terms-and-conditions.html)
