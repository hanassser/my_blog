---
title: 'Java Data Structures - Collections and Map'
date: '2024/4/5'
lastmod: '2022/3/10'
tags: [yes]
draft: true
summary: '///'
images: [/static/images/jds.png]
layout: PostLayout
---

## Time to check out the documentation again! :P
## Why there are Collection Interface and Collection Class
The Collection interface **defines the contract** for classes representing collections of objects, the Collections class provides **utility methods** for performing common operations on collections. 
The separation between the interface and the utility class allows for flexibility and modularity in the Java Collections Framework, making it easier to work with collections in Java programs.

## Collections class
```Java
List<Integer> list = new ArrayList<>();
Collections.sort(list);
Collections.reverse(list);
Collections.shuffle(list);
int max = Collections.max(list);
int min = Collections.min(min);
Collections.addAll(list, 10, 12);
```

## Collection Interface
```Java
Set<Integer> set = new HashSet<>();
List<Integer> list = new ArrayList<>();
list.addAll(set);

// Convert Array to List
Integer[] arr = {1, 5, 7, 9};
List<Integer> list = Arrays.asList(arr);

```
## Map
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
