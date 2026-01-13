## Iterative

```csharp
int n = nums.Length;
int low = 0, high = n - 1;

while (low <= high) {
    int mid = (low + high) / 2;
    if (nums[mid] == target)
        return mid;
    else if (target > nums[mid])
        low = mid + 1;
    else
        high = mid - 1;
}
return -1;
```

### Time and Space

Time -
| Best Case | Average Case | Worst Case |
| --------- | ------------ | ---------- |
| O(1) | O(log n) | O(log n) |

Space - O(1)

---

## Recursion

```csharp
public static int binarySearch(int[] nums, int low, int high, int target) {
    if (low > high)
        return -1; // Base case.

    // Perform the steps:
    int mid = (low + high) / 2;
    if (nums[mid] == target)
        return mid;
    else if (target > nums[mid])
        return binarySearch_re(nums, mid + 1, high, target);
    return binarySearch(nums, low, mid - 1, target);
}
```

### Time and Space

Time -
| Best Case | Average Case | Worst Case |
| --------- | ------------ | ---------- |
| O(1) | O(log n) | O(log n) |

Space - O(log n)

---

### Problem: Potential integer overflow

This line is risky:

```csharp
int mid = (low + high) / 2;
```

If `low` and `high` are large, this can overflow.

### Production-safe version

```csharp
int mid = low + (high - low) / 2;
```

---
