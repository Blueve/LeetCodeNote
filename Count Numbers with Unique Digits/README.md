Count Numbers with Unique Digits
==========

## C++

O(N) Time (max(N) == 9)
```cpp
class Solution {
public:
    int countNumbersWithUniqueDigits(int n) {
        if(n < 0) return 0;
        if(n < 1) return 1;
        int count = 10, s = 9;
        for(int i = 1, p = 9; i < n && p; ++i)
        {
            s *= p--;
            count += s;
        }
        return count;
    }
};
```

O(1) Time
```cpp
class Solution {
public:
    int countNumbersWithUniqueDigits(int n) {
        const int result[] = {1, 10, 91, 739, 5275, 32491, 168571, 712891, 2345851, 5611771, 8877691};
        return n >= 0 ? result[n > 10 ? 10 : n] : 0;
    }
};
```