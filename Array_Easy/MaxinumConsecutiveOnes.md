## Example

Input: prices = {1, 1, 0, 1, 1, 1}
Output: 3

```csharp
int count = 0, maxCount = 0;

int[] arr = { 1, 1, 0, 1, 1, 1 };

for (int i = 0; i < arr.Length; i++)
{
    if (arr[i] == 1)
    {
        count++;
        if (maxCount < count)
            maxCount = count;
    }
    else
    {
        count = 0;
    }
}

Console.WriteLine(maxCount);
```

### Time and Space

Time - O(N)
Space - O(1)

---
