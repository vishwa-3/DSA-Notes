## Example

Input: arr[]={1,1,2,2,2,3,3}
Output: {1,2,3}

## Brute Force

Use an extra array called `result` and store non-duplicate values by checking one by one.

### Time and Space

Time - O(N^2)
Space - O(N)

---

## Unsorted

```csharp
public static int[] RemoveDuplicates(int[] arr)
{
    HashSet<int> set = new HashSet<int>();
    List<int> result = new List<int>();

    foreach (int x in arr)
    {
        if (!set.Contains(x))
        {
            set.Add(x);
            result.Add(x);
        }
    }

    return result.ToArray();
}
```

### Time and Space

Time - O(N)
Space - O(N)

---

## Sorted

```csharp
int[] arr = { 1, 1, 1, 2, 2, 3, 3, 4, 4 };

int p1 = 0;

for (int p2 = 1; p2 < arr.Length; p2++)
{
    if (arr[p1] != arr[p2])
    {
        p1++;
        arr[p1] = arr[p2];
    }
}

// Print unique elements
for (int i = 0; i <= p1; i++)
{
    Console.WriteLine(arr[i]);
}
```

### Time and Space

Time - O(N)
Space - O(1)

> This is only works for `sorted array`.

---
