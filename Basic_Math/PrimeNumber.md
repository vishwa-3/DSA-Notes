## Example:

Input:N = 2  
Output:True

## Brute Force

```csharp
public static bool CheckPrime(int n) {
    int counter = 0;

    for (int i = 1; i <= n; i++) {
        if (n % i == 0) {
            counter++;
        }
    }
    return (counter == 2); // 1 is not a prime number
}
```

### Time and Space

Time - O(N)
Space - O(1)

---

## Better

```csharp
public static bool CheckPrime(int n) {
    int counter = 0;

    for (int i = 1; i <= Math.Sqrt(n); i++) {
        if (n % i == 0) {
            counter++;

            if (i != n / i) {
                counter++;
            }
        }

    }
    return (counter == 2);
}
```

### Time and Space

Time - O(sqrt(N))
Space - O(1)

> Why 1 - Sqrt(n)? already explain in divisors problem.

---

## Optimize

```csharp
public static bool CheckPrime(int n) {
    if (n <= 1)
        return false;

    for (int i = 2; i * i <= n; i++) // also use i<=sqrt(n)
        if (n % i == 0)
            return false;

    return true;
}
```

### Time and Space

Time - O(sqrt(N))
Space - O(1)

---
