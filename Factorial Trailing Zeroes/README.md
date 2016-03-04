Factorial Trailing Zeroes
==========

## C++

Every factor which suffix is 5 lead to a zero

```cpp
class Solution {
public:
    int trailingZeroes(int n) {
        int result(0);
        for(long long i(5); i <= n; i *= 5)
        {
            result += n / i;
        }
        return result;
    }
};
```

```cpp
class Solution {
public:
    int trailingZeroes(int n) {
        return n == 0 ? 0 : n / 5 + trailingZeroes(n / 5);
    }
};
```
