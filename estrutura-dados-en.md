Here are some common sorting algorithms used in programming:

1. **Bubble Sort**: This simple sorting algorithm iterates over a list, comparing each pair of adjacent items and swapping them if they are in the wrong order. The pass through the list is repeated until no swaps are needed, indicating that the list is sorted.

2. **Selection Sort**: This is an in-place comparison sorting algorithm. It has O(n^2) time complexity, making it inefficient on large lists, and generally performs worse than the similar insertion sort.

3. **Insertion Sort**: This is a simple sorting algorithm that builds the final sorted array one item at a time. It is much less efficient on large lists than more advanced algorithms such as quicksort, heapsort, or merge sort.

4. **Quick Sort**: This is a divide and conquer algorithm. It works by selecting a 'pivot' element from the array and partitioning the other elements into two sub-arrays, according to whether they are less than or greater than the pivot.

5. **Merge Sort**: This is also a divide and conquer algorithm. It works by dividing the unsorted list into n sublists, each containing one element (a list of one element is considered sorted), and repeatedly merging sublists to produce new sorted sublists until there is only one sublist remaining.

6. **Heap Sort**: This is a comparison-based sorting algorithm. It can be thought of as an improved selection sort: like that algorithm, it divides its input into a sorted and an unsorted region, and it iteratively shrinks the unsorted region by extracting the largest element and moving that to the sorted region.

7. **Radix Sort**: This is a non-comparative integer sorting algorithm that sorts data with integer keys by grouping keys by the individual digits which share the same significant position and value.

8. **Bucket Sort**: This is a comparison sort algorithm that operates on elements by dividing them into different buckets and then sorting these buckets individually. Each bucket is sorted individually using a separate sorting algorithm or by applying the bucket sort algorithm recursively.

9. **Shell Sort**: This is a generalization of insertion sort that allows the exchange of items that are far apart. The idea is to arrange the list of elements so that, starting anywhere, considering every hth element gives a sorted list.

10. **Counting Sort**: This is a simple sorting algorithm that works on the keys that are small integers; it counts the number of objects that have each distinct key value, and use arithmetic on those counts to determine the positions of each key value in the output sequence.

Each of these sorting algorithms has its own strengths and weaknesses, and is best suited to specific types of tasks and data.