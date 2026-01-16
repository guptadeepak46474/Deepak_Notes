# Number Theory Concepts

## whether a number has exactly 4 divisors


```

```



```python
def has_exactly_4_divisors(n):
    # Case 1: n = p^3
    p = round(n ** (1/3))
    if p**3 == n and is_prime(p):
        return True

    # Case 2: n = p * q (p != q)
    for i in range(2, int(math.sqrt(n)) + 1):
        if n % i == 0:
            p, q = i, n // i
            return p != q and is_prime(p) and is_prime(q)

    return False
```
