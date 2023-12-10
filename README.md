Frequency of Element in Java
Here, on this page, we will discuss the program to find the frequency of elements in  Java programming language. We are given an array and need to print the frequency of each given element.

Frequency of element in Java
Java program to find the frequency of each element in the array
Methods Discussed are :
Objective: Java Program to find the Frequency of each element in the Array.

Method 1 : Using Naive Approach with extra space.
Method 2 : Naive way without extra space.
Method 3 : Using Sorting
Method 4 : Using hash Map
Let’s discuss each method one by one,

Method 1 :
In this method we will count the frequency of each elements using two for loops.

To check the status of visited elements create a array of size n.
Run a loop from index 0 to n and check if (visited[i]==1) then skip that element.
Otherwise create a variable count = 1 to keep the count of frequency.
Run a loop from index i+1 to n
Check if(arr[i]==arr[j]), then increment the count by 1 and set visited[j]=1.
After complete iteration of for loop print element along with value of count.
Time and Space Complexity :
Time Complexity : O(n2)
Space Complexity : O(n)
Method 1: Code in Java
Run
import java.util.Arrays;
class Main
{
public static void countFreq(int arr[], int n)
{
boolean visited[] = new boolean[n];
Arrays.fill(visited, false);

// Traverse through array elements and
// count frequencies
for (int i = 0; i < n; i++) {

// Skip this element if already processed
if (visited[i] == true)
continue;

// Count frequency
int count = 1;
for (int j = i + 1; j < n; j++) {
if (arr[i] == arr[j]) {
visited[j] = true;
count++;
}
}
System.out.println(arr[i] + " occurs " + count +" times ");
}
}

// Driver code
public static void main(String []args)
{
int arr[] = new int[]{10, 30, 10, 20, 10, 20, 30, 10};
int n = arr.length;
countFreq(arr, n);
}
}
Output
10 occurs 4 times

30 occurs 2 times

20 occurs 2 times
Related Pages
Sort first half in ascending order and second half in descending

Sort the elements of an array

Sorting elements of an array by frequency

Finding the Longest Palindrome in an Array

Counting Distinct Elements in an Array

Method 2 :
In this method we will use the naive way to find the frequency of elements in the given integer array without using any extra space.

Method 2 : Code in Java
Run
// Time Complexity : O(n^2)
// Aux Space Complexity : O(1)

import java.lang.*;

class Main
{
    public static void main (String[] args) {
        int[] arr = {5, 8, 5, 7, 8, 10};
        int size = arr.length;
        countFrequency(arr, size);
    }

    static void countFrequency(int[] array, int size)
    {

        for (int i = 0; i < size; i++){
            int flag = 0;
            int count = 0;

            for (int j = i+1; j < size; j++){
                if (array[i] == array[j]){
                    flag = 1;
                    break;
                }
            }

           // The continue keyword is used to end the current iteration 
           // in a for loop (or a while loop), and continues to the next iteration
            if (flag == 1)
                continue;

            for (int j = 0;j<=i;j++){
                if (array[i] == array[j])
                    count++;
            }
            System.out.println(array[i]+": "+count);
        }
    }
}
Output
5 : 2
7 : 1
8 : 2
10 : 1
Method 3 :
In this method we will sort the array then, count the frequency of the elements.

Time and Space Complexity :
Time Complexity : O(nlogn)
Space Complexity : O(1)
Method 3 : Code in Java
Run
import java.lang.*;
import java.util.Arrays;

class Main
{
    public static void main (String[] args) {
        int[] arr = {5, 8, 5, 7, 8, 10};
        int size = arr.length;
        countFrequency(arr, size);
    }

    static void countFrequency(int[] arr, int n)
    {

        Arrays.sort(arr);

        // Traverse the sorted array
        for (int i = 0; i < n; i++)
        {
            int count = 1;

            // Move the index ahead whenever
            // you encounter duplicates
            while (i < n - 1 && arr[i] == arr[i + 1]) {
                i++;
                count++;
            }

            System.out.println(arr[i] + ": " + count);


            count++;
        }
    }
}
Output
5 : 2
7 : 1
8 : 2
10 : 1
Method 4 :
In this method we will count use hash-map to count the frequency of each elements.

Declare a hash map.
Start iterating over the entire array
If element is present in map, then increase the value of frequency by 1.
Otherwise, insert that element in map.
After complete iteration over array, start traversing map and print the key-value pair.
Time and Space Complexity :
Time Complexity : O(n)
Space Complexity : O(n)
Frequency of element in java
Method 4 : Code in Java
Run
import java.util.*;
import java.util.Arrays;

class Main
{
   static void countFreq(int arr[], int n)
   {
      Map<Integer, Integer> mp = new HashMap<>();

      // Traverse through array elements and
      // count frequencies
      for (int i = 0; i < n; i++)
      {
         if (mp.containsKey(arr[i]))
         {
           mp.put(arr[i], mp.get(arr[i]) + 1);
         }
         else
         {
           mp.put(arr[i], 1);
         }
     }
     // Traverse through map and print frequencies
     for (Map.Entry<Integer, Integer> entry : mp.entrySet())
     {
          System.out.println(entry.getKey() + " occurs " + entry.getValue()+" times ");
     }
  }
  // Driver code
  public static void main(String []args)
  {
       int arr[] = new int[]{10, 30, 10, 20, 10, 20, 30, 10};
       int n = arr.length;
       countFreq(arr, n);
  }
}
Output
20 occurs 2 times

10 occurs 4 times

30 occurs 2 times
