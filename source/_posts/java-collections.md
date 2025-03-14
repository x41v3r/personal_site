---
title: The Collections Framework
date: 2025-03-06 20:46:06
categories:
- Java
tags:
---

# 1 Introducing the Collections Framework

The Collections Framework was first introduced in Java SE 2, in 1998 and was rewritten twice since then:

* in Java SE 5 when generics were added;
* in Java 8 when lambda expressions were introduced, along with default methods in interfaces.

These two are the most important updates of the Collections Framework that have been made so far. But in fact, almost every version of the JDK has its set of changes to the Collections Framework.

The amount of interfaces and classes in the Collections Framework may be overwhelming at first.

# 2 Collection Hierarchy

<img src="/images/java-collection-hierarchy.png">

## 2.1 Extending Collection with List

### 2.1.1 Choosing Implementation of the List Interface

The difference between a `List` of elements and a `Collection` of elements, is that a `List` remembers in what order its elements have been added.

### 2.1.2 Accessing the Elements Using an Index

## 2.2 Extending Collection with Set

I don't use this implementation.

# 2 The Stream API

# FastJson

Convert a JSONObject instance to a JSON string.

```java
String str1 = jsonObject.toString();  // str1 doesn't contain the key-values whose is null

String str2 = JSONObject.toJSONString(jsonObject, SerializerFeature.WriteMapNullValue);  //the key-values with a null value is contained in str2
```


