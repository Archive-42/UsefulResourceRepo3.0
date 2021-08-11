<span class="underline"></span>

<span class="underline"></span>

## Hash Tables

1.  [Hash Tables](hash-tables.html)
2.  [Complexity](hash-tables-complexity.html)
3.  [Hash Table Load Factor and Capacity](hash-table-load-factor-and-capacity.html)
4.  [Hash Table vs Hash Set](hash-table-vs-hash-set.html)
5.  [Open vs Closed Addressing](hash-tables-open-vs-closed-addressing.html)
6.  [Open Addressing](hash-tables-open-addressing.html)
7.  Coalesced Hashing
8.  [Cuckoo Hashing](cuckoo-hashing.html)
9.  [Robin Hood Hashing](robin-hood-hashing.html)
10. [Hopscotch Hashing](hopscotch-hashing.html)
11. [2-Choice Hashing](2-choice-hashing.html)
12. [2-Left Hashing](2-left-hashing.html)
13. [Linked Hash Table](linked-hash-table.html)
14. [Why large prime numbers are used in hash tables](prime-numbers-in-hash-tables.html)

## References

[Design and Analysis of Coalesced Hashing](https://books.google.com/books/about/The_Design_and_Analysis_of_Coalesced_Has.html?id=AudQAAAAMAAJ)  
<span style="color: grey; font-style: italic; font-size: smaller">by J. S. Vitter, W. C. Chen</span>

[Implementations for Coalesced Hashing](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.119.6552&rep=rep1&type=pdf)  
<span style="color: grey; font-style: italic; font-size: smaller">by J. S. Vitter</span>

[Deletion Algorithms for Coalesced Hashing](https://academic.oup.com/comjnl/article/29/5/436/486218)  
<span style="color: grey; font-style: italic; font-size: smaller">by W. C. Chen, J. S. Vitter</span>

<span class="underline"></span>

## Top Algorithm Articles

1.  [Dynamic programming vs memoization vs tabulation](dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](sliding-window-example.html)
4.  [What makes a good loop invariant?](what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](random-point-within-circle.html)

[**See all algorithm articles**](algorithms.html)

# Coalesced Hashing

Coalesced hashing is a technique for implementing a hash table. It's an [open addressing](hash-tables-open-addressing.html) technique which means that all keys are **stored in the array itself** (e.g. it doesn't use for example linked lists to handle collisions). As opposed to other open addressing techniques however, it also uses **nodes with next-poiners** to form collision chains.

**Example:** Coalesced hash table holding five keys in two collision chains. (Keys of the same color hash to the same bucket.)

k k k k k

## Insertion

Suppose we're inserting a key that hashes to slot _i_. If slot _i_ is empty, we insert it there and we're done. If it's not empty, we traverse the chain of next-pointers until we find the key (in which case we return) or until we reach the end of the chain. Suppose that we reach the end of the chain and that the last node in the chain is stored in slot _j_. We now look for a free slot by scanning from the bottom up. Suppose we find a free slot at index _k_. The key is inserted in slot _k_ and the next-pointer in slot _j_ is set to point to slot _k_.

**Example:** We have the following hash table…

0: 90 1: 2: 92 3: 14 4: 5: 6: 7: 72 8: 88 9: 32

…and we want to insert the key 52, which happens to hash to slot 2.

Slot 2 is not empty, so we traverse the chain: 92… 32… 72. We do not find 52 and slot 7 holds the last node in the chain.

We now search for an empty slot by scanning the table from the bottom up. We find slot 6 to be empty. We insert 52 in this slot, and append it to the chain by updating the next-pointer in slot 7.

0: 90 1: 2: 92 3: 14 4: 5: 6: 52 7: 72 8: 88 9: 32

### Coalesced Chains

If a key that hashes to slot _i_ is stored in slot _k_, what happens when another key is inserted, that hashes to slot _k_? The insertion algorithm will follow the same procedure; the new key will be inserted in an empty slot, and the chain starting in (or, running through) slot _k_ will be extended to include this key. At this point, both keys that hash to slot _i_ and keys that hash to slot _k_ will be stored in **the same collision chain**. We say that the chains are **coalesced**, hence the name of the algorithm.

**Example:** (Continuing from previous example.) We recall that key 52 (which hases to slot 2) was inserted in slot 6. Now we insert key 16 which hases to slot 6.

The insert procedure inserts the key in slot 5 and updates the next pointer in slot 6 to point to slot 5.

0: 90 1: 2: 92 3: 14 4: 5: 16 6: 52 7: 72 8: 88 9: 32

As can be seen the collision chain for slot 2 has been coaleced with the chain for slot 6.

### Variations

The insertion algorithm described above is called **late-insertion** as it appends the new node to the **end** of the chain. There's also **early-insertion** which inserts the key **immediately after** the original slot, and then reroutes the pointers accordingly. A third method is called **varied-insertion** which works like early-insertion but with a special case for when there is a so called cellar slot (discussed later) following its' hash address in the chain.

J. S. Vitter elaborates on this in the paper [Implementations for Coalesced Hashing](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.119.6552&rep=rep1&type=pdf).

## Lookup

If a key is not found in the slot it hashes to, the lookup algorithm follows the chain starting in that slot, and continues until the key is found or the chain ends.

**Note:** Due to coalescing, the chain can contain unrelated keys, i.e. keys that do not hash to the same slot as the key we're looking for.

## Removal

Simply clearing out a slot might break a chain, and cause future lookups to fail. To avoid this problem, one could instead use ‘deleted’ markings (see [Hash Tables: Open Addressing](hash-tables-open-addressing.html), section Removal) but this is subject to so called contamination.

The approach commonly used in practice is to clear the slot holding the key, and then **reinsert** all following keys in the chain.

This maintains the invariants, avoids contamination and potentially even breaks apart previously coalesced chains.

**Example:** In this example the hash function is `key % 10`. As can be seen in the left-most figure below, the chain for keys hashing to 2 (blue color) and the chain for keys hashing to 8 (red color) have been coalesced.

We now remove key 32, and reinsert 18, 32, 28 and 42:

0: 1: 12 2: 3: 4: 5: 28 6: 42 7: 18 8: 32 9: 22 To remove → 12 22 To reinsert: 18 , 42 , 28 12 28 42 18 22

For details, refer to the article [Deletion Algorithms for Coalesced Hashing](https://academic.oup.com/comjnl/article/29/5/436/486218) by W. C. Chen, and J. S. Vitter which also includes details for late, early, and varied insertion.

## Rehashing

As with all variants of hash tables, performance degrades as the load factor increases and, as usual, the threshold at which to rehash is a space–time tradeoff. The optimal limit also depends on wheather you want to optimize the runtime for failing or successful lookups.

The performance degrades rapidly as the load factor surpasses 50%. The paper [Implementations for Coalesced Hashing](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.119.6552&rep=rep1&type=pdf) suggests using 68% in a practical setting.

Being an open-addressing techinque, the theoretical maximum is 1.0.

## Performance

The longer the average length of the chains are, the longer the expected lookup time is. For this reason coalescing is bad for performance. (Two chains of length _L_<sub>1</sub> and _L_<sub>2</sub> are better than one chain of length <span class="no-wrap">_L_<sub>1</sub> + *L*<sub>2</sub></span>.)

The chains do however still help the lookup algorithm skip over irrelevant slots and mitigate the effects of primary and secondary clustering. (See sections on linear and quadratic probing in article [Hash Tables: Open Addressing](hash-tables-open-addressing.html).) The downside is the size overhead due to next-pointers and the extra level of indirection which affects cache performance.

### Runtime Complexity

In worst case, all keys hash to the same slot, and we get one long chain. Thus in worst case the the runtime complexity is **linear** (applies to all operations). Under the simple uniform hashing assumption (see [Hash Tables: Complexity](hash-tables-complexity.html)) the **amortized runtime is constant** for all operations.

## The Cellar

A common optimization (so common in fact, that it is almost to be considered a part of the standard implementation) is to reserve part of the hash table array to be used only for storing colliding keys. This part is called **the cellar**.

In a table of size _M_ with a cellar of size _N_, the slot, _i_, to which a key, _k_, belongs is computed as follows:

*i* = hash(_k_) % (M − N)

**Example:** A coalescing hash table array with <span class="no-wrap">*M* = 10</span> and <span class="no-wrap">*N* = 3</span>.

The addressable part: The slots to which keys can hash to. The cellar: Slots used when dealing with collisions.

When storing a key in the cellar, it does not interfere with other addressable slots and can thus not cause two chains to coalesce. In other words, the cellar acts as a **buffer against coalescing**. The idea is very similar to the so called stash used in [Cuckoo Hashing](cuckoo-hashing.html).

The cellar can also improve the performance of a removal operation. Since storing a key in the cellar never causes coalescing, keys stored in the cellar are easy to remove. You simply clear out the slot and rewire the pointers. There's no need to reinsert the keys in the tail of the chain to maintain the structural invariants.

Choosing how many slots of the full array to reserve for the cellar is a tradeoff:

Fewer cellar slots More addressable space Less coalescing Less need for cellar slots More cellar slots Less addressable space More coalescing More need for cellar slots

The optimal size of the cellar varies depending on the load factor, but according to the analysis in [Implementations for Coalesced Hashing](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.119.6552&rep=rep1&type=pdf) a **good overall value is 14%** of the total number of slots available.

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](terms-and-conditions.html)
