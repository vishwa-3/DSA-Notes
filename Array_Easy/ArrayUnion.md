## Example

Input:n = 5,m = 5 arr1[] = {1,2,3,4,5} arr2[] = {2,3,4,4,5}
Output: {1,2,3,4,5}

```csharp
int[] arr1 = { 1, 2, 3, 4, 5 };
int[] arr2 = { 2, 3, 4, 4, 5, 5, 6, 7, 8 };

int n = arr1.Length;
int m = arr2.Length;

int[] result = new int[n + m];
int i = 0, j = 0, k = 0;

while (i < n && j < m)
{
    if (arr1[i] < arr2[j])
    {
        if (k == 0 || result[k - 1] != arr1[i])
            result[k++] = arr1[i];
        i++;
    }
    else if (arr1[i] > arr2[j])
    {
        if (k == 0 || result[k - 1] != arr2[j])
            result[k++] = arr2[j];
        j++;
    }
    else
    {
        if (k == 0 || result[k - 1] != arr1[i])
            result[k++] = arr1[i];
        i++;
        j++;
    }
}

while (i < n)
{
    if (k == 0 || result[k - 1] != arr1[i])
        result[k++] = arr1[i];
    i++;
}

while (j < m)
{
    if (k == 0 || result[k - 1] != arr2[j])
        result[k++] = arr2[j];
    j++;
}

Console.Write("Union: ");
for (int x = 0; x < k; x++)
{
    Console.Write(result[x] + " ");
}


/*
int[] arr1 = { 1, 2, 3, 4, 5 };
int[] arr2 = { 2, 3, 4, 4, 5, 6 };

HashSet<int> set = new HashSet<int>();

foreach (int x in arr1) set.Add(x);
foreach (int x in arr2) set.Add(x);

foreach (int x in set)
    Console.Write(x + " ");
*/



```

### Time and Space

Time - O(n+m)
Space - O(n+m)

| Case                | Most Optimized |
| ------------------- | -------------- |
| Arrays are sorted   | Two-pointer    |
| Arrays are unsorted | HashSet        |

---
