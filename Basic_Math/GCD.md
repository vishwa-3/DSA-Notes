## Example:

Input: N1 = 9, N2 = 12
Output: 3

**GCD (Greatest Common Divisor)** is the largest positive integer that divides two numbers without leaving a remainder.

## Brute Force

```csharp
public static int GCD(int n1, int n2)
{
    int gcd = 1;

    for (int i = 1; i <= Math.Min(n1, n2); i++)
    {
        if (n1 % i == 0 && n2 % i == 0)
        {
            gcd = i;
        }
    }

    return gcd;
}
```

### Time and Space

Time - O(min(N1, N2))
Space - O(1)

---

## Better

```csharp
public static int GCD(int n1, int n2)
{
    for (int i = Math.Min(n1, n2); i >= 1; i--)
    {
        if (n1 % i == 0 && n2 % i == 0)
        {
            return i;
        }
    }

    return 1;
}
```

### Time and Space

Time - O(min(N1, N2))
Space - O(1)

> with less iteration

---

## Optimize

**Euclidean Algorithm**

It is a fast method to find the GCD of two numbers by repeatedly replacing the larger number with the remainder of dividing it by the smaller number until the remainder becomes 0.

```csharp
public static int GCD(int n1, int n2) {
    while (n1 > 0 && n2 > 0) {
        // If n1 is greater than n2, subtract n2 from n1 and update n1
        if (n1 > n2) {
            // Update n1 to the remainder of n1 divided by n2
            n1 = n1 % n2;
        }
        // If n2 is greater than or equal to n1, subtract n1 from n2 and update n2
        else {
            // Update n2 to the remainder of n2 divided by n1
            n2 = n2 % n1;
        }
    }
    // Check if n1 becomes 0,
    // if so, return n2 as the GCD

    // If n1 is not 0,
    // return n1 as the GCD

    return n1 == 0 ? n2 : n1;
}
```

### Time and Space

Time - O(log(min(n1, n2)))
Space - O(1)

---

## Recursion

```csharp
public static int GCD(int n1, int n2)
{
    if (n2 == 0)
        return n1;

    return GCD(n2, n1 % n2);
}
```

### Time and Space

Time - O(log(min(n1, n2)))
Space - O(log(min(n1, n2)))

---
