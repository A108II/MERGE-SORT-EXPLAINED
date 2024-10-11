# Merge Sort Documentation

The merge sort algorithm is a **divide and conquer** sorting technique. It recursively splits the array into smaller subarrays, sorts them, and then merges them back together using the `merge` function.

## Merge Sort Algorithm

1. **Divide**: Split the array into two halves recursively until each subarray has one element.
2. **Conquer**: Use the `merge` function to combine sorted subarrays into a single sorted array.

### Code

```javascript
function mergeSort(array) {
    if (array.length <= 1) {
        return array;  // Base case
    }

    const middle = Math.floor(array.length / 2);
    const left = mergeSort(array.slice(0, middle));  // Recursively split left half
    const right = mergeSort(array.slice(middle));    // Recursively split right half

    return merge(left, right);  // Merge the sorted halves
}
```

## Merge Function

The `merge` function takes two sorted arrays and combines them into a single sorted array.

### Code

```javascript
function merge(firstArray, secondArray) {
    let combinedArray = [];
    let i = 0;
    let j = 0;

    while(i < firstArray.length && j < secondArray.length) {
        if(firstArray[i] < secondArray[j]) {
            combinedArray.push(firstArray[i]);
            i++;
        } else {
            combinedArray.push(secondArray[j]);
            j++;
        }
    }

    while(i < firstArray.length) {
        combinedArray.push(firstArray[i]);
        i++;
    }

    while(j < secondArray.length) {
        combinedArray.push(secondArray[j]);
        j++;
    }

    return combinedArray;
}
```

### Example Usage

```javascript
mergeSort([5, 3, 8, 4, 2, 7, 1, 6]);  // Returns [1, 2, 3, 4, 5, 6, 7, 8]
```

## Complexity

- **Time Complexity**: O(n log n) – The array is recursively divided in half (log n), and each level of recursion requires merging n elements.
- **Space Complexity**: O(n) – Requires additional space proportional to the array size for temporary storage during merging.

