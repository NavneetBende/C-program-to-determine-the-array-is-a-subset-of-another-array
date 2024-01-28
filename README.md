Array is a subset of another array in C
In this section we will determine the program to find if an Array is a subset of another array in C . If all the elements of array 2 are found in array 1, then array 2 is said to be a subset of array 1.

Array is a subset of another array in C
While loop in C
Example
arr1 = {1,2,3,4,5}  , arr2 = {3,4,5}
arr2 is a subset of arr1 (As, arr1 contains all the elements of arr2)
arr3 = {1,2,3,4,5}   arr4 = {1,2,9}
arr4 is not a subset of arr3 (As, arr3 do not contains all the elements of arr4).
Here, we will discuss the following methods,

Method 1 : Using nested loops
Method 2 : Using sorting and binary search.
Method 3 : Using sorting and merging.
Method 1 :
Run a loop for loo from index 0 to length of arr2
Run a inner loop from index 0 to length of arr2
If(arr2[i]==arr1[j]), then break the inner loop
Check if(j==m) then return 0.
Otherwise, return 1.
Method 1 : Code in C
//Write a program to check whether Array is a subset of another array in C
#include <stdio.h>

int isSubset(int arr1[], int arr2[], int m, int n)
{
    int i = 0;
    int j = 0;
    for (i = 0; i < n; i++) {
        for (j = 0; j < m; j++) {
            if (arr2[i] == arr1[j])
                break;
        }
 
        if (j == m)
           return 0;
    }
 
    return 1;
}
 
// Driver code
int main()
{
    int arr1[] = { 11, 10, 13, 21, 30, 70 };
    int arr2[] = { 11, 30, 70, 10 };
 
    int m = sizeof(arr1) / sizeof(arr1[0]);
    int n = sizeof(arr2) / sizeof(arr2[0]);
 
    if (isSubset(arr1, arr2, m, n))
        printf("arr2[] is subset of arr1[] ");
    else
        printf("arr2[] is not a subset of arr1[]");
 
    return 0;
}
Output :
arr2[] is subset of arr1[]
Related Pages
Find maximum product sub-array in a given array

Finding Arrays are disjoint or not

Determine can all numbers of an array be made equal

Finding Minimum sum of absolute difference of given array

Sort an array according to the order defined by another array 

Method 2 :
In this method we first sort arr1 then, using binary search we find the elements of arr2 in arr1

Sort arr1[]
For each element of arr2[], do binary search for it in sorted arr1[].
If the element is not found then return 0.
If all elements are present then return 1.
Method 2 : Code in C
// Write a program to check whether Array is a subset of another array in C
#include<stdio.h>

int binarySearch(int arr[], int low, int high, int x);

int isSubset(int arr1[], int arr2[], int m, int n)
{
    int i = 0;
 
    for (i = 0; i < n; i++) {
     if (binarySearch(arr1, 0, m - 1, arr2[i]) == -1) 
        return 0; 
     } 
     return 1;
}

int binarySearch(int arr[], int low,int high, int x) { if (high >= low)
    {
        /*low + (high - low)/2;*/
        int mid = (low + high) / 2;
 
        if ((mid == 0 || x > arr[mid - 1]) && (arr[mid] == x))
            return mid;
        else if (x > arr[mid])
            return binarySearch(arr, (mid + 1), high, x);
        else
            return binarySearch(arr, low, (mid - 1), x);
    }
    return -1;
}
 
// Driver code
int main()
{
    int arr1[] = { 11, 10, 13, 21, 30, 70 };
    int arr2[] = { 11, 30, 70, 10 };
 
    int m = sizeof(arr1) / sizeof(arr1[0]);
    int n = sizeof(arr2) / sizeof(arr2[0]);
    
    for(int i=0; iarr1[j]){
                int temp = arr1[i];
                arr1[i] = arr1[j];
                arr1[j] = temp;
            }
        }
    }
    if (isSubset(arr1, arr2, m, n))
        printf("arr2[] is subset of arr1[] ");
    else
        printf("arr2[] is not a subset of arr1[]");
 
    return 0;
}
Output :
arr2[] is subset of arr1[]
