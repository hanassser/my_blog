---
title: 'Java Data Structures - Collections and Map'
date: '2024/4/14'
lastmod: '2022/3/10'
tags: [Java, Data Structures]
draft: false
summary: 'Time to check out the documentation again! And think about the big O, time complexity and space complexity! Remember data structure is used to store and operate data.'
images: [/static/images/jds.png]
layout: PostLayout
---

### 💥 Time to check out the `documentation` again! 
### 💥 Think about the big O, `time complexity` and `space complexity`!  
### 💥 Remember data structure is used to store and operate data.
---

## Why there are Collection Interface and Collection Class
The Collection interface **defines the contract** for classes representing collections of objects, the Collections class provides **utility methods** for performing common operations on collections. 
The separation between the interface and the utility class allows for flexibility and modularity in the Java Collections Framework, making it easier to work with collections in Java programs.

### Collections class
```Java
List<Integer> list = new ArrayList<>();
Collections.sort(list);
Collections.reverse(list);
Collections.shuffle(list);
int max = Collections.max(list);
int min = Collections.min(min);
Collections.addAll(list, 10, 12);
```

### Collection Interface

```Java
Set<Integer> set = new HashSet<>();
List<Integer> list = new ArrayList<>();
list.addAll(set);

// Convert Array to List
Integer[] arr = {1, 5, 7, 9};
List<Integer> list = Arrays.asList(arr);

```
---

## ArrayList, LinkedList
![](/static/images/list.png)  

I'm gonna compare these two in aspects of 👇👇👇
- `Underlying Data Structure`
  - ArrayList: uses a dynamic array to store elements. Elements are stored in a contiguous block of memory, and accessing elements by index is fast because it involves simple array indexing.
  - LinkedList: uses a doubly linked list data structure. Each element(node) contains a reference to the previous and next elements, allowing for efficient insertion and deletion operations but slower random access. 
- `Performance` 
  - Random Access(get/set)
    - ArrayList: random access operations are `O(1)` time complexity, very efficient, coz they directly access elements by index.
    - LinkedList: `O(n)` time complexity, coz it requires traversing the list from the beginning to end to search the desired index.
  - Insertion/Deletion
    - ArrayList: 
    - LinkedList: 
- `Memory Overhead`  
  ArrayList generally has less memory overhead per element compared to LinkedList because it doesn't need to store references to previous and next elements. 

- `Iterating` 
  - 
- `Usage Scenarios`
  - ArrayList: Use ArrayList when you need fast random access and when the list size doesn't change frequently.
  - LinkedList: Use LinkedList when frequent insertion/deletion operations are expected, especially at the beginning or end of the list, and when random access is less important.

---
## Map 
First, we should know `Hashtable` is a class that implements `Map` interface.
Check out this [video](https://www.youtube.com/watch?v=KyUTuwz_b7Q&ab_channel=ComputerScience). It really helps me understand Hash Tables and Hash Functions.  
Basically, `Hash Table` is a data structure that allows very fast retrieval of data no matter the size of the data or the position of the data (retrieval by index, index is calculated by hash function). It means on average, retrieve an element by index is O(1) time complexity (constant time).
For this reason, it's wildly used in **database indexing**, **caching**, **program compilation**, **error checking** and more.  
Then, the three most used class that implement `Map` interface are `HashMap`, `TreeMap` and `LinkedHashMap`. Look at their name, we can guess how they are implemented.
- `HashMap` are designed for rapid access. 
- `TreeMap` keeps its keys in sorted order, thus is not as fast as a `HashMap`. 
- `LinkedHashMap` keeps its element in insertion order, but provides rapid access with hashing.

```java
Map<String, Integer> map = new HashMap<>();
map.put("bike", 2);
map.put("book", 6);
map.get("bike");
map.remove("bike");
map.containsKey("book");
map.containsValue("6");
map.size();
map.clear();
map.keySet();
map.getOrDefault("book", 0);
map.isEmpty();

```

## PriorityQueue
```java
PriorityQueue<String, Integer> queue = new PriorityQueue<>();
queue.poll();
queue.add();

```
