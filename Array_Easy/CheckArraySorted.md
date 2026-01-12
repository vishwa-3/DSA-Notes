## Example

Input: arr[] = {2, 5, 1, 3, 0}  
Output: false

```csharp
public static bool IsSorted(int[] arr)
{
    bool isSorted = true;

    for (int i = 0; i < arr.Length - 1; i++)
    {
        if (arr[i] > arr[i + 1])
        {
            isSorted = false;
            break;
        }
    }

    return isSorted;
}
```

### Time and Space

Time - O(N)
Space - O(1)

---
