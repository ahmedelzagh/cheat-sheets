# Euclidean algorithm

The Euclidean algorithm is a method for finding the greatest common divisor (GCD) of two numbers. The GCD is the largest positive integer that divides both numbers without leaving a remainder.

The algorithm works by dividing the larger number by the smaller number and finding the remainder. If the remainder is zero, then the smaller number is the GCD. If the remainder is not zero, then the algorithm is repeated with the smaller number as the new larger number and the remainder as the new smaller number. The algorithm continues in this way until the remainder is zero, and the final non-zero remainder is the GCD.

For example, consider the two numbers `a = 60` and `b = 48`. To find their GCD, we can divide `a` by `b`:

```
60 / 48 = 1 R 12
```

Since the remainder `12` is not zero, we repeat the process with `b` as the new larger number and `12` as the new smaller number:

```
48 / 12 = 4 R 0
```

Since the remainder is zero, we have found the GCD, which is `12`.

The Euclidean algorithm is simple to implement and has many applications in computer science, including cryptography and computer graphics.