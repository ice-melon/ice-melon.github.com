---
layout: post
title: "pick a random element from a long array"
date: 2013-08-24 22:53
comments: true
categories: English algorithm 
---
Suppose you have an array of n elemnets and you have to pick an element randomly. It is easy that you just pick each element with probability 1/n.

While if you don't know the size of the array, you receive the element one at a time. How to pick the element? In theory you could wait for all elements to come and compute the probility. But the stream may be too large to be stored in memory, which makes it infeasible. We want an algorithm that we do not have to store the elements and look at the elements twice.

Here comes the solution:

    1.Choose the first element with probability 1
	2.Replace the first element with the second element, with probability 1/2
	3.Replace the current element with the third element, with probability 1/3
	4.Continue doing this until the stream ends.


Let's prove the correctness by induction:

	Suppose that after seeing n-1 elements, each of the first n-1 elements is chosen with equal probability.  
	When you see the nth element, it is chosen with probability 1/n, and each of the other elements is chosen
	with probability [1/(n-1)] * [(n-1) / n] = 1/n. 
	Therefore all elements are chosen with equal probability.

The algorithm takes O(1) space and O(n) time, which is quite simple and beautiful. 
For more information, see [Reservior sample](http://en.wikipedia.org/wiki/Reservoir_sampling) on Wikipedia.
