## Example:

Input: N = 36
Output: [1, 2, 3, 4, 6, 9, 12, 18, 36]

## Brute Force

```csharp
public static void PrintDivisors(int n)
{
    List<int> arr = new List<int>();

    for (int i = 1; i <= n; i++)
    {
        if (n % i == 0)
        {
            arr.Add(i);
        }
    }

    foreach (int d in arr)
    {
        Console.WriteLine(d);
    }
}
```

### Time and Space

Time - O(N)
Space - O(N)

---

## Optimize

if `d` is a divisor of `n` then **`n/d` is also a divisor of `n`**.

For every divisor `d <= √n`, there is a matching divisor `n/d >= √n`.

For `n = 36`, if `d = 3` is a divisor, then `n/d = 12` is also a divisor (since 36 = 3 × 12), and here 3 ≤ √36 = 6 while 12 ≥ 6.

```csharp
public static void PrintDivisors(int n)
{
    List<int> arr = new List<int>();

    for (int i = 1; i * i <= n; i++)   // better than Math.Sqrt inside loop
    {
        if (n % i == 0)
        {
            arr.Add(i);

            if (i != n / i) // n = 36 if(6 != 6)
                arr.Add(n / i);
        }
    }

    foreach (int d in arr)
    {
        Console.WriteLine(d);
    }
}
```

### Time and Space

Time - O(sqrt(N))
Space - O(sqrt(N))

---
