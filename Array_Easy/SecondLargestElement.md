## Example

Input: arr[] = {2, 5, 1, 3, 0}  
Output: 3

```csharp
int[] arr = { 2, 5, 1, 3, 0, 10 };

if (arr == null || arr.Length < 2)
    throw new ArgumentException("Array must contain at least two elements");

int firstMax = int.MinValue;
int secondMax = int.MinValue;

for (int i = 0; i < arr.Length; i++) {
    if (arr[i] > firstMax) {
        secondMax = firstMax;
        firstMax = arr[i];
    } else if (arr[i] > secondMax && arr[i] != firstMax) {
        secondMax = arr[i];
    }
}

if (secondMax == int.MinValue)
        throw new InvalidOperationException("No second largest element");

return secondMax;
```

### Time and Space

Time - O(N)
Space - O(1)

---
