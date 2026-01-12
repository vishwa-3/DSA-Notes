## Example

Input: 1 ,0 ,2 ,3 ,0 ,4 ,0 ,1
Output: 1 ,2 ,3 ,4 ,1 ,0 ,0 ,0

```csharp
public static int[] MoveZero(int[] arr)
{
    int n = arr.Length;
    int j = -1;

    for (int i = 0; i < n; i++)
    {
        if (arr[i] == 0)
        {
            j = i;
            break;
        }
    }

    if (j == -1)
        return arr;

    for (int i = j + 1; i < n; i++)
    {
        if (arr[i] != 0)
        {
            int tmp = arr[i];
            arr[i] = arr[j];
            arr[j] = tmp;
            j++;
        }
    }

    return arr;
}
```

### Time and Space

Time - O(N)
Space - O(1)

---
