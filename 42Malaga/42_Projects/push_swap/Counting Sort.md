Counting sort is a non-comparison sorting algorithm that works by counting the occurrences of each unique element in the input array and then constructing the output array based on these counts. However, when dealing with negative numbers, counting sort requires an offset to map the negative indices to the correct positions in the auxiliary array.

Offset Calculation

To accommodate negative numbers, calculate the offset as follows:

`offset = 0 - minValue`

where `minValue` is the smallest number in the input array. This offset ensures that the negative indices are correctly mapped to the auxiliary array.

**Example**

Suppose the input array contains the elements `-2`, `0`, `1`, `3`, and `-5`. The minimum value is `-5`, so the offset would be `offset = 0 - (-5) = 5`.

Auxiliary Array Indexing

When counting the occurrences of each element, use the following formula to calculate the auxiliary array index:

`index = element + offset`

For example, the element `-2` would be counted at index `-2 + 5 = 3` in the auxiliary array.

Sorting

To sort the output array, iterate through the input array in reverse order (from largest to smallest) and place each element at its correct position in the output array, decrementing the corresponding count in the auxiliary array.

Stability

Counting sort is a stable sorting algorithm, meaning that the order of equal elements is preserved. When sorting negative numbers, this stability ensures that the order of equal negative values is maintained.

Code Modifications

To modify a counting sort implementation to accommodate negative numbers, make the following changes:

1. Calculate the offset using the minimum value of the input array.
2. Update the auxiliary array indexing formula to include the offset.
3. Adjust the sorting logic to account for the offset when placing elements in the output array.

Example Code

In Java, the modified counting sort algorithm would look like this:
```java
public void sort(int[] arr) {
    int min = Integer.MINVALUE;
    int max = Integer.MAXVALUE;
    for (int i = 0; i < arr.length; i++) {
        if (arr[i] < min) {
            min = arr[i];
        }
        if (arr[i] > max) {
            max = arr[i];
        }
    }
    int offset = 0 - min;
    int[] counts = new int[max - min + 1];
    for (int i = 0; i < arr.length; i++) {
        counts[arr[i] + offset]++;
    }
    // ... rest of the sorting logic ...
}
```
By incorporating these modifications, counting sort can efficiently sort arrays containing negative numbers while maintaining stability and correctness.