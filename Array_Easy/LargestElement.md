## Example

Input: arr[] = {2, 5, 1, 3, 0}  
Output: 5

## Iteration

```csharp
public static int FindMax(int[] arr)
{
    int max = arr[0];

    for (int i = 1; i < arr.Length; i++)
    {
        if (arr[i] > max)
        {
            max = arr[i];
        }
    }

    return max;
}
```

### Time and Space

Time - O(N)
Space - O(1)

---

## Recursion

```csharp
public static int FindMax(int[] arr, int i, int max)
{
    if (i == arr.Length)
    {
        return max;
    }

    if (arr[i] > max)
    {
        max = arr[i];
    }

    return FindMax(arr, i + 1, max);
}
```

### Time and Space

Time - O(N)
Space - O(N)

---
