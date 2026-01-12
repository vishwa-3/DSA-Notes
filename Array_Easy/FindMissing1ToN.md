## Example

Input Format: N = 5, array[] = {1,2,4,5}
Result: 3

```csharp
int[] arr = { 1, 2, 4, 5 };
int n = arr.Length + 1;

int expectedSum = n * (n + 1) / 2;
int actualSum = 0;

foreach (int num in arr)
{
    actualSum += num;
}

return expectedSum - actualSum;
```

### Time and Space

Time - O(N)
Space - O(1)

If `N = 100,000`, then:

`N * (N + 1)`

> can overflow int.

**Production-safe version:**

> long expectedSum = (long)n \* (n + 1) / 2;

---

## Even More Optimized (XOR Method)

```csharp
int xor1 = 0, xor2 = 0;

for (int i = 1; i <= n; i++)
    xor1 ^= i;

foreach (int num in arr)
    xor2 ^= num;

return xor1 ^ xor2;
```

### Time and Space

Time - O(N)
Space - O(1)

- I can solve it using sum formula in O(N), but it risks overflow.
- XOR method avoids overflow and keeps O(1) space.

---
