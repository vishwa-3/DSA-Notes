## Example

Input : nums = [1, 2, 3, 4, 5, 6, 7], k = 2
Output : [6, 7, 1, 2, 3, 4, 5]

## Brute Force

Use **Rotate by one** and call k times

### Time and Space

Time - O(N \* K)
Space - O(1)

---

## Optimize

```csharp
class RotateByK
{
    static void ReverseArray(int[] arr, int start, int end)
    {
        int l = start, r = end - 1;
        while (l < r)
        {
            int temp = arr[l];
            arr[l] = arr[r];
            arr[r] = temp;
            l++;
            r--;
        }
    }

    static void PrintArray(int[] arr)
    {
        foreach (int i in arr)
        {
            Console.Write(i + " ");
        }
        Console.WriteLine();
    }

    static void Main()
    {
        int[] arr = { 1, 2, 3, 4, 5, 6, 7 };
        int k = 2;
        int n = arr.Length;

        k = k % n;

        ReverseArray(arr, 0, n);
        ReverseArray(arr, 0, k);
        ReverseArray(arr, k, n);

        PrintArray(arr);
    }
}
```

### Time and Space

Time - O(N) + O(N) + O(N - K) = O(N)
Space - O(1)

**Steps:**

- Reverse whole array
- Reverse first k elements
- Reverse remaining n-k elements

---
