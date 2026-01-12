## Reverse the number

```csharp
public static int Reverse(int n) {
    int rev = 0;
    while (n > 0) {
        int ld = n % 10;

        // 1534236469 - 9646324351 -> overflow
        if (rev > int.MaxValue / 10 || (rev == int.MaxValue / 10 && ld > 7))
            return 0;

        if (rev < int.MinValue / 10 || (rev == int.MinValue / 10 && ld < -8))
            return 0;

        rev = (rev * 10) + ld;
        n /= 10;
    }

    return rev;
}
```

If `rev > 214748364`, then `rev \* 10` will already be more than **2147483640**
Adding any digit will overflow
`rev == Integer.MAX_VALUE / 10 && digit > 7`
**Edge case:** if rev is exactly **214748364**
You can only safely add 7 or less `(since MAX_VALUE = 2147483647)`

### Time and Space

Time - O(log10N)
Space - O(1)

```csharp
public static void ReverseUsingString(int n) {
   string s = n.ToString();
    char[] arr = s.ToCharArray();
    Array.Reverse(arr);
    Console.WriteLine(new string(arr));
}
```

| Operation         | Cost |
| ----------------- | ---- |
| `n.ToString()`    | O(d) |
| `ToCharArray()`   | O(d) |
| `Array.Reverse()` | O(d) |
| `new string(arr)` | O(d) |

> Since d = log10(n)

### Time and Space

Time - O(log10N)
Space - O(log10N)

---

## Palindrome Brute Force

```csharp
public static bool isPalindrome(int n) {
    if (n < 0)
        return false;
    return n == Reverse(n);
}
```

### Time and Space

Time - O(log10N)
Space - O(1)

---

## Palindrome Optimize

```csharp
public static bool isPalindrome_OP(int n) {
    // Negative numbers or numbers ending in 0 and 0 itself are not palindrome
    if (n < 0 || (n % 10 == 0 && n != 0)) return false;

    int reversedHalf = 0;

    while (n > reversedHalf) {
        int ld = n % 10;
        reversedHalf = reversedHalf * 10 + ld;
        n /= 10;
    }

    // For even digits: n == reversedHalf
    // For odd digits: n == reversedHalf / 10 (middle digit can be ignored)
    return (n == reversedHalf || n == reversedHalf / 10);
}

```

### Time and Space

Time - O(log10N)
Space - O(1)

---
