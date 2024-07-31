# Merge Sort

* Introduction to Merge Sort
    • Merge Sort is a more time-efficient sorting algorithm compared to simple sorting methods like bubble sort and insertion sort
    • It uses a divide and conquer approach:
        1. Divide the unsorted array into halves
        2. Conquer by recursively sorting each half
        3. Merge the sorted halves back together

* Merge Sort Algorithm
    1. Divide: split the array into two halves
    2. Conquer: recursively sort each half
    3. Merge: Combine the two sorted halves into one sorted array

* Example
To sort the array '[10, 1, 7, 2]':
    1. Divide: `[10, 1]` and `[7, 2]`
    2. Sort each half: `[1, 10]` and `[2, 7]`
    3. Merge: `[1, 2, 7, 10]`

* Merge Function
    • Merge takes two sorted arrays and combines them into one sorted array
    • Compare the first elements of each array, move the smaller element to the result array, and repeat until all the elements are sorted

* Example:
    • Arrays: `[1, 10]` and `[2, 7]`
    • Merge steps:
        - compare `1` and `2`, move `1` to result
        - compare `10` and `2`, move `2` to result
        - compare `10` and `7`, move `7` to result
        - add remaining `10` to result
    • Result `[1, 2, 7, 10]`

* Time Complexity of Merge
    • The merge operation runs in O(n) time
    • It uses pointers to compare elements without mutating the original arrays

* Recursive Function
    • Recursion is used to call the merge sort function on each half
    • Base case: an array of length 1 or 0 is already sorted

* Steps:
    1. Call merge sort recursively to sort left and right halves
    2. Merge the sorted halves
    3. Repeat until the array is fully sorted

* Time Complexity of Merge Sort
    • Merge sort has time complexity of O(n log n):
        - merging takes O(n)
        - dividing the array take O(log n)

* Space Complexity of Merge Sort
    • Each recursive call creates new arrays, leading to O(n log n) space complexity
    • In-place merge sort can reduce space complexity to O(1), but requires iterative implementation

* Merge Sort Pseudocode
```js
function mergeSort(arr) {
    // check if the input is length 1 or less
    if (arr.length <= 1) return arr;

    // divide the array in half
    const mid = Math.floor(arr.length / 2);
    const left = arr.slice(0, mid);
    const right = arr.slice(mid);

    // recursively sort the left half
    // recursively sort the right half
    // merge the halves together and return
    return merge(mergeSort(left), mergeSort(right));
}

// takes in two sorted arrays and returns them merged into one
function merge(arrA, arrB) {
    const result = [];
    let i = 0, j = 0;

    // while there are still values in each array...
    while(i < arrA.length && j < arrB.length) {
        // compare first values of each array
        // add the smaller value to the return array
        // move the pointer to the next value in that array
        if (arrA[i] < arrB[j]) {
            result.push(arrA[i]);
            i++;
        } else {
            result.push(arrB[j]);
            j++;
        }
    }

    // add any remaining elements from arrA
    while (i < arrA.length) {
        result.push(arrA[i]);
        i++;
    }

    // add any remeaining elements from arrB
    while (j < arrB.length) {
        result.push(arrB[j]);
        j++;
    }

    // return merged array
    return result;
}
```

* Key Takeaways
    • Merge sort is a recursive sorting algorithm using a divide and conquer strategy
    • It has a time complexity of O(n log n)
    • Space complexity is O(n log n) due to the additional arrays created during the merge process
    • An in-place merge sort can reduce space complexity but is more complex to implement
