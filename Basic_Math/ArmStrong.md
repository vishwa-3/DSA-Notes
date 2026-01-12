## Example:

Input:N = 153
Output:True

An Armstrong number is a number that is equal to the sum of its digits each raised to the power of the total number of digits.

153 = 1³ + 5³ + 3³ = 1 + 125 + 27 = 153

So, 153 is an Armstrong number.

```csharp
public static bool IsArmstrong(int n)
{
    if (n == 0) return true;

    int x = n;
    int d = 0;

    while (x > 0)
    {
        x /= 10;
        d++;
    }

    x = n;
    int sum = 0;

    while (x > 0)
    {
        int ld = x % 10;
        int pow = 1;

        for (int i = 0; i < d; i++)
            pow *= ld;

        sum += pow;
        x /= 10;
    }

    return sum == n;
}
```

### Time and Space

Time - O((log10 N)²)
Space - O(1)

Why not to use `Math.Pow()` in Armstrong number check: ` O(log10 N. log log10 N)`

- Returns double – not precise for large integers
- May cause rounding issues.
- Slower for integers
- Internally uses floating-point operations.
- Extra type conversion
- You’ll need to cast back to int, which can lead to wrong results.

---
