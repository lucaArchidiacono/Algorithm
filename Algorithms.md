# Algorithms:

## Search
At the moment I only know two categories of search algorithms I'll need to learn:
- Linear
- Binary

>The linear and binary algorithms are named as such to describe how long (time complexity) a search is going to take based on the size of the input that is being search

### Linear search
With linear search algorithms, I have to search at every item in the input before I came across my desired value. It is called linear because the time is takes to search is exactly correlated with the amount of items in the search (100 items/input =100 checks/complexity).

For example:

When I try to find my friend Paul among a line of people standing in no particular order, I simply have to look at each person, one by one, in sequence, until I recognize or fail to recognize Paul. And that's it. In doing so, I'm following the linear search algorithm.

```java
class LinearSearch { 
    // This function returns index of element x in arr[]
    /**
    * String arr[]: An array with all the people
    * int n: Length of array
    * String x: Person I'm searching. In this case Paul.
    */
    static int search(String arr[], int n, String x) 
    { 
        for (int i = 0; i < n; i++) { 
            // Return the index of the element if the element 
            // is found 
            if (arr[i] == x) 
                return i; 
        } 
  
        // return -1 if the element is not found 
        return -1; 
    } 
} 
```
### Binary search
Binary search gets its name because the word binary means “of or relating to 2 things” and the algorithm works by splitting the input into two parts until it finds the item that is being searched. One half contains the search item and the other half doesn’t. The process continues until the spot where the input is split becomes the item that is being searched. Binary search is basically just a highly disciplined approach to the process of elimination. It’s faster than linear search, but it only works with ordered sequences.

For example:

Suppose I'm trying to find my friend Daniel (who is 174cm) in a single-file line of people that have been ordered by height from left to right, shortest to tallest. It’s a really long line, and I don’t have time to go one-by-one through the whole thing, comparing everyone’s height to Daniel's.

With binary search I select the person in the very middle of the line, and measure their height. They’re 180cm. So right away I know that this person, along with everyone to their right, is not Daniel. Now that I've cut my problem in half, I turn my attention to the remainder of the line and pick the middle person again. They’re 165cm. So I can rule out that person and anyone to their left, cutting the problem in half again. And so on. After just five or six of these splits, I quickly home in on Daniel in a fraction of the time it took me to find Paul.

```Java
class BinarySearch { 
    // Returns index of x if it is present in arr[l.. 
    // r], else return -1 
    /**
    * int arr[]: An array with the heights of people
    * int n: Length of array
    * int x: Height I'm searching. In this case Daniel's 174.
    */
    int binarySearch(int arr[], int l, int r, int x) 
    { 
        if (r >= l) { 
            int mid = l + (r - l) / 2; 
  
            // If the element is present at the 
            // middle itself 
            if (arr[mid] == x) 
                return mid; 
  
            // If element is smaller than mid, then 
            // it can only be present in left subarray 
            if (arr[mid] > x) 
                return binarySearch(arr, l, mid - 1, x); 
  
            // Else the element can only be present 
            // in right subarray 
            return binarySearch(arr, mid + 1, r, x); 
        } 
  
        // We reach here when element is not present 
        // in array 
        return -1; 
    } 
  
    // Driver method to test above 
    public static void main(String args[]) 
    { 
        BinarySearch ob = new BinarySearch(); 
        int arr[] = { 2, 3, 4, 10, 40 }; 
        int n = arr.length; 
        int x = 10; 
        int result = ob.binarySearch(arr, 0, n - 1, x); 
        if (result == -1) 
            System.out.println("Element not present"); 
        else
            System.out.println("Element found at index " + result); 
    } 
} 
```
---

## Sorting
Ordering, otherwise know as sorting, lists of items is one of the most common programming tasks I'll do as a developer. Those are one of the most useful sorting algorithms: 
- MergeSort
- QuickSort

### MergeSort
It divides input array in two halves, calls itself for the two halves and then merges the two sorted halves. The merge() function is used for merging two halves.

For Example:

The following diagram from wikipedia shows the complete merge sort process for an example array {38, 27, 43, 3, 9, 82, 10}. If we take a closer look at the diagram, we can see that the array is recursively divided in two halves till the size becomes 1. Once the size becomes 1,the merge processes comes into action and starts merging arrays back till the complete array is merged.

![alt text](https://www.geeksforgeeks.org/wp-content/uploads/Merge-Sort-Tutorial.png "MergeSet example from Wikipedia")

![alt text](https://cdn-images-1.medium.com/max/1600/1*d9AkauyhqsMZcLFYhrY3DQ.gif "MergeSet example as GIF")