# Activity 12.2: Merge Sort

## My Code:
```
public class MergeSort {
    private static int comp = 0;
    private static int swap = 0;
    public static void merge(int[] numbers, int i, int j, int k) {
        int mergedSize = k - i + 1;       // Size of merged partition
        int mergedNumbers[] = new int[mergedSize]; // Temporary array for merged numbers
        int mergePos;                     // Position to insert merged number
        int leftPos;                      // Position of elements in left partition
        int rightPos;                     // Position of elements in right partition

        mergePos = 0;
        leftPos = i;                      // Initialize left partition position
        rightPos = j + 1;                 // Initialize right partition position

        // Add smallest element from left or right partition to merged numbers
        while (leftPos <= j && rightPos <= k) {
            if (numbers[leftPos] < numbers[rightPos]) {
                mergedNumbers[mergePos] = numbers[leftPos];
                ++leftPos;
            } else {
                mergedNumbers[mergePos] = numbers[rightPos];
                ++rightPos;
            }
            ++mergePos;
            comp++;
        }

        // If left partition is not empty, add remaining elements to merged numbers
        while (leftPos <= j) {
            mergedNumbers[mergePos] = numbers[leftPos];
            ++leftPos;
            ++mergePos;
            swap++;
        }

        // If right partition is not empty, add remaining elements to merged numbers
        while (rightPos <= k) {
            mergedNumbers[mergePos] = numbers[rightPos];
            ++rightPos;
            ++mergePos;
            swap++;
        }

        // Copy merge number back to numbers
        for (mergePos = 0; mergePos < mergedSize; ++mergePos) {
            numbers[i + mergePos] = mergedNumbers[mergePos];
        }
    }

    public static void mergeSort(int[] numbers, int i, int k) {
        int j;

        if (i < k) {
            j = (i + k) / 2;  // Find the midpoint in the partition

            // Recursively sort left and right partitions
            mergeSort(numbers, i, j);
            mergeSort(numbers, j + 1, k);

            // Merge left and right partition in sorted order
            merge(numbers, i, j, k);
        }
    }
    public int getComp()
    {
        return comp;
    }
    public int getSwap()
    {
        return swap;
    }
}
```

```
import java.util.Scanner;

public class Main
{
    public static void main(String [] args) {
        MergeSort a = new MergeSort();
        Scanner reader = new Scanner(System.in);
        int [] arr;
        System.out.println("Enter the size of an integer array, followed by the elements of the array (no duplicates):");
        int size = reader.nextInt();
        arr = new int[size];//set size

        System.out.print("UNSORTED: ");
        for (int i = 0; i < arr.length; ++i) {
            arr[i]= reader.nextInt();
            System.out.print(arr[i] + " ");
        }
        System.out.println();

        /* initial call to merge sort with index */
        a.mergeSort(arr, 0, arr.length - 1);

        System.out.print("SORTED: ");
        for (int i = 0; i < arr.length; ++i) {
            System.out.print(arr[i] + " ");
        }
        System.out.println();

        System.out.println("swaps: " + a.getSwap());
        System.out.println("comparisons: " + a.getComp());
    }
}
```

## Challenges:
This activity was a lttle easier than the last one because of its similarity. I just had to apply the same concept I used for the insertion sort to merge sort.
