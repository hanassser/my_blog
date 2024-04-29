---
title: "Sorting and Searching Algorithms"
date: '2024/4/24'
lastmod: '2022/3/10'
tags: [Sorting, searching, algorithms]
draft: false
summary: "DP = Recursion + Memorization"
images: [/static/images/ss.png]
layout: PostLayout
---
## Common sorting algorithms
- `Bucket Sort`  
  Runtime:  average and worst case. Memory: .
- `Merge Sort`  **Recursion** + **Divide and Conquer**   
  Runtime: O(nlog(n)) average and worst case. Memory: depends.
  ```java
  public class MergeSort {
    private static void mergeSort(int[] arr) {
        int n = arr.length;
        if (n < 2) {
            return;
        }

        int mid = n / 2;
        int[] leftHalf = new int[mid];
        int[] rightHalf = new int[n - mid];

        for (int i = 0; i < mid; i++) {
            leftHalf[i] = arr[i];
        }
        for (int i = mid; i < n; i++) {
            rightHalf[i - mid] = arr[i];
        }

        mergeSort(leftHalf);
        mergeSort(rightHalf);
        merge(arr, leftHalf, rightHalf);
    }

    private static void merge (int[] arr, int[] leftHalf, int[] rightHalf) {
        int leftSize = leftHalf.length;
        int rightSize = rightHalf.length;

        int i = 0, j = 0, k = 0;
        while (i < leftSize && j < rightSize) {
            if (leftHalf[i] <= rightHalf[j]) {
                arr[k] = leftHalf[i];
                i++;
            }
            else {
                arr[k] = rightHalf[j];
                j++;
            }
            k++;
        }
        while (i < leftSize) {
            arr[k] = leftHalf[i];
            i++;
            k++;
        }
        while (j < rightSize) {
            arr[k] = rightHalf[j];
            j++;
            k++;
        }
    }
  } 
  ```
  
- `Quick Sort`  **Recursion** + **Pivot**
  Runtime: O(nlog(n)) average, O(n^2) worst case. Memory: O(nlog(n)).
`Arrays.sort()` is based on a variation of the quicksort algorithm, called the dual-pivot quicksort algorithm.
- `Bubble Sort`  
  Runtime: O(n^2) average and worst case. Memory: O(1).
- `Selection Sort`
  Runtime: O(n^2) average and worst case. Memory: O(1).
- `Insertion Sort`  
  Runtime: O(n^2) average and worst case. Memory: O(1).
  ```Java
  public class InsertionSort {
    public static void doInsertionSort(int[] a){
        int n = a.length;
        for(int i = 1; i < n; i++){
            int key = a[i];
            int j = i - 1;
            while(j >= 0 && a[j] > key){
                a[j + 1] = a[j];
                j--;
            }
            a[j + 1] = key;
        }
    }
  }
  ```

## Searching algorithms
- Binary Search
- maybe using a Hash Table

## Some exercises
- `Sorted Merge`: You are given two `sorted arrays`, A and B, where A has a large enough buffer at the
end to hold B. Write a method to merge B into A in sorted order.
    ```java
    public static void merge(int[] a, int[] b, int sa, int sb){
      int indexA = sa-1;
      int indexB = sb-1;
      int indexMerge = sa+sb-1;

      // merge a and b, starting from the last element in each
      while(indexB >= 0){
          if(indexA >= 0 && a[indexA] > b[indexB]){
              a[indexMerge] = a[indexA];
              indexA--;
          } else {
              a[indexMerge] = b[indexB];
              indexB--;
          }
          indexMerge--;
      }
    }
    ```

- `Group Anagrams`: Write a method to sort an array of strings so that all the anagrams are next to each other.
   ```java
    class Anagram {
        private String sortChars(String s){
            char[] content = s.toCharArray();
            Arrays.sort(content);
            return new String(content);
        }
        private void sort(String[] arr){
            Map<String, List<String>> mapList = new HashMap<>();
            for(String s: arr){
                String key = sortChars(s);
                if(!mapList.containsKey(key)){
                    mapList.put(key, new ArrayList<>());
                }
                mapList.get(key).add(s);
            }
            int index = 0;
            for(String key: mapList.keySet()){
                List<String> list = mapList.get(key);
                for(String s: list){
                    arr[index++] = s;
                }
            }
        }
    }
   ```
- `Search in Rotated Array`: Given a sorted array of n integers that has been rotated an unknown number of times, write code to find an element in the array. You may assume that the array was originally sorted in increasing order,
  EXAMPLE
  Input:find5in[15, 16, 19, 20, 25, 1, 3, 4, 5, 7, 10, 14} Output: 8 (the index of 5 in the array)

- `Sorted Search, No Size`: You are given an array-like data structure Listy which lacks a size method. It does, however, have an elementAt(i) method that returns the element at index i in O(1) time, if i is beyond the bounds of the data structure, it returns -1. (For this reason, the data structure only supports positive integers.) 
  Given a List y which contains sorted, positive integers, find the index at which an element X occurs. If x occurs multiple times, you may return any index.
