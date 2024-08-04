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

    // add any remaining elements from arrB
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


# Quicksort

* Overview
Quicksort is an efficient, recursive divide-and-conquer sorting algorithm. It typically performs better than other O(n log n) algorithms like merge sort due to better cache performance and low overhead.

* Algorithm Steps
    1. Choose a Pivot: select a value from the array to serve as the pivot. This can be any value but is often the first element
    2. Partition: rearrange the array so that all elements less than the pivot come before it, and all elements greater than the pivot come after it
    3. Recursively Sort Partitions: apply the same process to the left and right partitions
    4. Combine: return the array by combining the sorted left partition, pivot, and sorted right partition

* Example

Sort the array [5, 4, 10, 1, 8, 3, 6]:

    1. Choose Pivot: 5
    2. Partition:
        • Left: [4, 1, 3]
        • Right: [10, 8, 6]

    3. Recursively Sort Partitions:
        • Left Sorted: [1, 3, 4]
        • Right Sorted: [6, 8, 10]

    4. Combine:
        • [1, 3, 4] + 5 + [6, 8, 10] -> [1, 3, 4, 5, 6, 8, 10]

* Recursive Sorting
Quicksort recursively sorts subarrays, reducing their size each time until reaching arrays of length 1 or 0, which are inherently sorted

* Time Complexity
    • Average Case: O(n log n) due to efficient partitioning
    • Worst Case: O(n^2) when pivot selection leads to highly unbalanced partitions, e.g. sorting an already sorted array with the first element as pivot

* Space Complexity
    • Out-of-place: O(n log n) due to creating new arrays for partitions
    • In-Place: O(1) if implemented without additional arrays, modifying the input array directly

Pseudocode
```js
function quicksort(arr) {
    // base case: arrays of length 1 or less are already sorted
    if (arr.length <= 1) return arr;

    // pick a pivot
    let pivot = arr[0]
    let left = [], right = [];

    // partition array into left and right
    for (let i = 1; i < arr.length; i++) {
        if (arr[i] < pivot) left.push(arr[i]);
    } else right.push(arr[i]);

    // recursively sort partitions and combine with pivot
    return [...quicksort(left), pivot, ...quicksort(right)];
}
```

* In-Place Quicksort
To improve space efficiency, in-place quicksort modifies the input array without additional arrays. It uses a pointer technique to swap elements, ensuring all smaller elements are on one side of the pivot and all larger elements on the other

* Key Takeaways
    • Divide and Conquer: quicksort splits the array around a pivot and recursively sorts subarrays
    • Recursive Approach: achieves efficient sorting by reducing problem size of each call
    • Performance: average time complexity is O(n log n); worst-case is O(n^2), which can be mitigated with good pivot selection strategies
    • Space Complexity: Out-of-place O(n log n), in-place O(1)

Understanding quicksort's mechanism and implementing it both out-of-place and in-place enhances problem-solving skills in sorting and algorithm optimisation.


# Funky Sorting

* Key Concepts
    1. In-Place Sorting:
        • Sort without using extra space (space complexity of O(1))
        • Common techniques: swapping and shifting elements in the array
    2. Optimal Sorting:
        • Minimise total number of operations (optimise time complexity)
        • Techniques to achieve O(n) time complexity in specific problems

* Problem: Zeroes to the Right

    Objective: Move all zeroes in the array to the end while maintaining the relative order of non-zero elements

    Constraints:
        • In-place algorithm
        • Minimise operations

    Plan:
    1. Use a pointer `firstZero` to track the left-most zero
    2. Iterate through the array:
        • If a zero is encountered, update `firstZero`
        • When a non-zero is encountered, swap it with the element at `firstZero` and increment `firstZero`

    Code:
    ```js
    function moveZeroes(nums) {
        let firstZero = -1; // pointer to the first zero

        for (let i = 0; i < nums.length; i++) {
            if (firstZero === -1) {
                if (nums[i] === 0) firstZero = i;
            } else if (nums[i] !== 0) {
                [nums[i], nums[firstZero]] = [nums[firstZero], nums[i]];
                firstZero++;
            }
        }
        return nums;
    }
    ```
    Explanation:
        • Efficiently swaps elements to move all zeroes to the end with minimal operations


* Problem: Even/Odd Sort

    Objective: Sort the array so that all even numbers are on the left and all odd numbers are on the right, both in ascending order

    Constraints:
        • No specific time or space requirements

    Plan:
        1. Create two empty arrays: `evens` and `odds`
        2. Iterate through the array:
            • Find the smallest even and odd values
            • Append these values to `evens` and `odds` respectively
            • Remove the smallest values from the original array
        3. Join `evens` and `odds` arrays

    ```js
    function evenOddSort(nums) {
        const evens = [];
        const odds = [];

        while (nums.length > 0) {
            let smallestEven = Infinity;
            let smallestOdd = Infinity;

            for (let i = 0; i < nums.length; i++) {
                if (nums[i] % 2 === 0 && nums[i] < smallestEven) {
                    smallestEven = nums[i];
                } else if (nums[i] % 2 === 1 && nums[i] < smallestOdd) {
                    smallestOdd = nums[i];
                }
            }

            if (smallestEven !== Infinity) {
                evens.push(smallestEven);
                nums.splice(nums.indexOf(smallestEven), 1);
            }

            if (smallestOdd !== Infinity) {
                odds.push(smallestOdd);
                nums.splice(nums.indexOf(smallestOdd), 1);
            }
        }

        return [...evens, ...odds];
    }
    ```
    Explanation:
        • Seperates and sorts evens and odds by iteratively finding and removing the smallest values

* What You Learned
    • In-Place Sorting: Techniques for optimising space complexity
    • Efficient Sorting: Strategies for minimising operations to achieve optimal time complexity
    • Custom Sorting: Applying sorting techniques to solve specific problems, such as seperating zeroes or sorting evens and odds
