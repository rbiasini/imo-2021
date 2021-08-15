## Problem 1
Let n > 100 be an integer. Ivan writes the numbers n, n + 1, . . . , 2n each on different
cards. He then shuffles these n + 1 cards, and divides them into two piles. Prove that at least one of
the piles contains two cards such that the sum of their numbers is a perfect square.


## Solution

The set of integers that can be obtained as a sum of 2 numbers in the range [n, 2n] is [2n+1, 4n-1].
The fundamental idea is to notice that the number of perfect squares in the range [2n+1, 4n-1] tends to grow as n grows.

To prove the thesis, it is sufficient to prove that, for a n sufficiently large (>100), it exists a trio of integers a, b, c, with a<b<c, such that:

```
{  
  a + b = x^2  
  a + c = y^2  
  b + c = z^2  
}
```

with
n <= a < b < c <= 2n and x, y, z being integers.
If this is true, then it would be impossible to divide the range [n...2n] in 2 piles so that no pair of numbers in each pile has their sum equal to a perfect square. Indeed, at least 2 numbers among the trio a, b, c must inevitably fall in the same pile.

More in particular, let's assume that x, y, z are consecutive numbers in the form of 2m - 1, 2m, 2m + 1, with m being an integer.
Basically 3 consecutive odd-even-odd numbers. 

We now have:

```
{
  a + b= (2m-1)^2  
  a + c = (2m)^2  
  b + c = (2m + 1)^2 
}
```

Note that if the consecutive numbers were even-odd-even, the system above would have no solution in the integer domain.
Through linear combinations of the equations of the linear system, we can rewrite it as:

```
{  
  a = 4m^2 - 4m  
  b = 4m^2 + 1  
  c = 4m^2 + 4m  
}
```

now we have to prove that, for n > 100, it is possible to find an integer m such that:

```
{
  4m^2 - 4m >= n  
  2m^2 + 2m <= n  
}
```

Solving the inequalities above, you get:

```
{
  m >= (1 + sqrt(1 + n)) / 2  
  m <= (-1 + sqrt(1 + 2n)) / 2  
}
```

We can conservatively add 1 to the right side of the first inequality. This is to make sure that an integer solution for m exists.

So, we now have:

```
{
  m >= (3 + sqrt(1 + n)) / 2  
  m <= (-1 + sqrt(1 + 2n)) / 2  
}
```

which has solutions for m only if:

```
(3 + sqrt(1 + n)) / 2 <= (-1 + sqrt(1 + 2n)) / 2  
```

The above inequality can be simplified to:

```
4 + sqrt(1 + n)  <= sqrt(1 + 2n)  
```

squaring both sides:

```
16 + 8 * sqrt(1 + n) + 1 + n  <= 1 + 2n  
```

which can be simplified to:

```
8 * sqrt(1 + n)  <= n - 16  
```

squaring again both sides and assuming that n > 16:

```
64 + 64n  <= n^2 - 32n + 256  
```

which is the same as:

```
n^2 - 96n + 192 > 0  
```

The above inequality is true for `n > 48 + 8*sqrt(33)`.  
Since `48 + 8*sqrt(33)` is lower than 96, then we proved the thesis for n > 100
