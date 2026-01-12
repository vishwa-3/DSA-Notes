## Example:

Input: N = 12345
Output: 5

## Brute Force

```csharp
public class CountDigit {

    public int CountDigits(int n) {
        int count = 0;
        while (n != 0) {
            n /= 10;
            count++;
        }

        return count;
    }
}
```

> safe and predictable

### Time and Space

Time - O(log10N + 1)
Space - O(1)

> Number of Digits = **Log10(N) + 1**
> log₁₀(10) = 1 → because 10¹ = 10
> log₁₀(100) = 2 → because 10² = 100

---

## Optimize

```csharp
public class CountDigit {

    public int CountDigits(int n) {
        if(n==0) return 1;  //Log10(0) is Undefined
        return (int)Math.Log10(n) + 1;
    }
}
```

> fast but risky

### When This Approach Is Dangerous

This approach uses floating point math. That can cause precision errors.

```cssharp
CountDigits(1000)
```

> Sometimes floating-point math gives 2.9999999 → cast to 2 → wrong.

### Time and Space

Time - O(1)
Space - O(1)

---
