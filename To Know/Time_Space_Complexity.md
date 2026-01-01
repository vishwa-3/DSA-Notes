## 1. Why Time & Space Complexity Exist

When we write code, two resources matter:

1. **Time** → How fast does the algorithm run as input grows?
2. **Memory (Space)** → How much extra memory does it consume?

We **do NOT measure**:

- Seconds
- CPU speed
- Machine performance

We measure **growth rate** as input size `n` increases.

This is called **asymptotic analysis**.

---

## 2. Big-O Notation

Big-O describes the **upper bound** (worst-case growth).

It answers:

> “How bad can this get when input becomes very large?”

Example:

- `O(n)` means time grows linearly with input size
- `O(n²)` means time grows quadratically

We **ignore**:

- Constants
- Smaller terms

Why? Because growth dominates.

---

## 3. Common Time Complexities

### O(1) — Constant Time

Time does **not depend on input size**

```csharp
int GetFirst(int[] arr)
{
    return arr[0];
}
```

Even if array has 10 or 10 million elements → **same time**

Best possible complexity

---

### O(log n) — Logarithmic Time

Input size reduces **by half each step**

```csharp
// Binary Search
int BinarySearch(int[] arr, int target)
{
    int low = 0, high = arr.Length - 1;

    while (low <= high)
    {
        int mid = (low + high) / 2;

        if (arr[mid] == target) return mid;
        else if (arr[mid] < target) low = mid + 1;
        else high = mid - 1;
    }

    return -1;
}
```

Each step:

- n → n/2 → n/4 → n/8 …

Very fast even for large inputs.

---

### O(n) — Linear Time

Work grows **directly proportional** to input

```csharp
int Sum(int[] arr)
{
    int sum = 0;
    foreach (int x in arr)
        sum += x;

    return sum;
}
```

Array size doubles → time doubles.

---

### O(n log n)

Common in **efficient sorting algorithms**

Examples:

- Merge Sort
- Quick Sort (average case)

```text
Divide problem → O(log n)
Process each level → O(n)
Total → O(n log n)
```

Used heavily in production systems.

---

### O(n²) — Quadratic Time

Nested loops over the same input

```csharp
void PrintPairs(int[] arr)
{
    for (int i = 0; i < arr.Length; i++)
    {
        for (int j = 0; j < arr.Length; j++)
        {
            Console.WriteLine(arr[i] + ", " + arr[j]);
        }
    }
}
```

If `n = 1000`, operations ≈ **1,000,000**

> Dangerous for large inputs

---

### O(2ⁿ) — Exponential Time

Each step doubles possibilities

```csharp
int Fibonacci(int n)
{
    if (n <= 1) return n;
    return Fibonacci(n - 1) + Fibonacci(n - 2);
}
```

Input grows slightly → time explodes.

Unacceptable for production

---

### O(n!) — Factorial Time

All permutations

```text
Traveling Salesman brute force
Permutations of array
```

Absolutely unusable beyond tiny inputs.

---

## 4. Drop Constants Rule

```text
O(2n)   → O(n)
O(5n²)  → O(n²)
O(n + 1000) → O(n)
```

We care about **growth**, not exact steps.

---

## 5. Multiple Loops — How to Calculate

### Same input, sequential loops

```csharp
for (int i = 0; i < n; i++) { }
for (int i = 0; i < n; i++) { }
```

Time = `O(n + n)` → **O(n)**

---

### Nested loops

```csharp
for (int i = 0; i < n; i++)
{
    for (int j = 0; j < n; j++)
    {
    }
}
```

Time = `O(n * n)` → **O(n²)**

---

### Different inputs

```csharp
void Example(int[] a, int[] b)
{
    foreach (var x in a) { }   // O(n)
    foreach (var y in b) { }   // O(m)
}
```

Time = **O(n + m)**

Do **NOT** blindly combine.

---

## 6. Space Complexity (Extra Memory Used)

Space complexity measures **additional memory**, not input memory.

### O(1) Space — Constant Space

```csharp
int Sum(int[] arr)
{
    int sum = 0;
    foreach (int x in arr)
        sum += x;
    return sum;
}
```

Only one variable → constant space.

---

### O(n) Space

```csharp
int[] Copy(int[] arr)
{
    int[] copy = new int[arr.Length];
    for (int i = 0; i < arr.Length; i++)
        copy[i] = arr[i];

    return copy;
}
```

Extra array of size `n` → O(n) space.

---

### Recursive Space (Stack Memory)

```csharp
int Factorial(int n)
{
    if (n == 0) return 1;
    return n * Factorial(n - 1);
}
```

Each call adds a stack frame.

Space = **O(n)** (call stack)

---

## 7. Time vs Space Trade-Off

Example: Checking duplicates

### Brute force

```csharp
// O(n²) time, O(1) space
```

### Using HashSet

```csharp
// O(n) time, O(n) space
```

Faster time costs more memory.

**This trade-off is everywhere in production systems.**

---

## 8. How Interviewers Expect You to Explain

You MUST say:

1. Time complexity
2. Space complexity
3. Why
4. Possible optimization

Example:

> “This solution runs in O(n) time because we traverse the array once.
> It uses O(1) extra space since no additional data structures are allocated.”

---
