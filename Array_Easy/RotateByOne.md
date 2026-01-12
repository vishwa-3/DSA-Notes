## Example

Input: arr[]={ 1, 2, 3, 4, 5 }
Output: { 2, 3, 4, 5, 1 }

```csharp
public static void RotateLeftByOne(int[] arr)
{
    if (arr == null || arr.Length <= 1)
        return;

    int first = arr[0];

    for (int i = 0; i < arr.Length - 1; i++)
        arr[i] = arr[i + 1];

    arr[arr.Length - 1] = first;
}
```

### Time and Space

Time - O(N)
Space - O(1)

---
