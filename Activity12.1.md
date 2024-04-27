# Activity 12.1: Insertion Sort

## My Code:
```
import java.util.Scanner;

public class InsertionSort {
    private static int comp = 0;
    private static int swap = 0;

    private static void printArray(int arr[])
    {
        for (int i = 0; i < arr.length; ++i)
            System.out.print(arr[i] + " ");
        System.out.println();
    }
    public void insertionSort(int[] arr)
    {
        int i;
        int j;
        int temp;      // temp variable for swap
        for (i = 1; i < arr.length; ++i) {
            j = i;
            // Insert numbers[i] into sorted part
            // stopping once numbers[i] in correct position
            while (j > 0 && arr[j] < arr[j - 1])
            {
                // Swap numbers[j] and numbers[j - 1]
                temp = arr[j];
                arr[j] = arr[j - 1];
                arr[j - 1] = temp;
                --j;
                swap ++;
            }
            comp++;
            printArray(arr);
        }
        System.out.println("comparisons: " + comp);
        System.out.println("swaps: " + swap);
    }
}
```

```
import java.util.Scanner;

public class Main
{
public static void main(String [] args)
{
    InsertionSort a = new InsertionSort();
    Scanner reader = new Scanner(System.in);
    int [] arr;
    System.out.println("Enter the size of an integer array, followed by the elements of the array (no duplicates):");
    int size = reader.nextInt();
    arr = new int[size];//set size
    for (int i = 0; i < size; ++i)//prints initial arr
    {
        arr[i]= reader.nextInt();
        System.out.print(arr[i] + " ");
    }
    System.out.println();
    System.out.println();

    a.insertionSort(arr);
}
}
```

## Challenges:
This activity was a little more challenging for me because I couldn't figure out how to count the number of comparisons vs swaps.
