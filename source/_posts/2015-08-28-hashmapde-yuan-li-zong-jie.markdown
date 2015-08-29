---
layout: post
title: "HashMap的原理总结"
date: 2015-08-28 17:59:57 +0200
comments: true
categories:  HashMap 数据结构
---


我们知道HashMap拥有高读取性能，the hash-map has O(1) access with **high probability** （注意是最理想情况是O(1)，但是相比O(n)更接近O(1)）。高读取性能数据结构背后具体是怎么实现的呢，这篇笔记就一起来总结下。

Basically, a hash table is an array containing all of the keys to search on. The position of each key in the array is determined by the *hash function*, which can be any function which always maps the same input to the same output.

### hashcode() and equals() 方法
参考原文地址：http://www.java2blog.com/2014/02/hashcode-and-equals-method-in-java.html

These methods can be found in the Object class and hence available to all java classes. Using these two methods, an object can be stored or retrieved from a Hashtable, HashMap or HashSet.

1. **hashcode():**
 You might know if you put entry in HashMap, first hashcode is calculated and this hashcode used to find bucket(index) where this entry will get stored in hashMap.You can read more at How hashMap works in java. What if you don't override hashcode method, it will return integer representation of memory address.


2. **equals():**
  You have to override equals method, when you want to define equality between two object. If you don't override this method, it will check for reference equality(==) i.e. if tow reference refers to same object or not.

### HashMap的结构java实现
