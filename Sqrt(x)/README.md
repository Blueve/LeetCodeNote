Sqrt(x)
==========

## C++

Bisection
```cpp
class Solution {
public:
    int mySqrt(int x) {
        long long l(0), r(x + 1L), m(0), t;
        while(l < r)
        {
            m = l + (r - l >> 1);
            t = m * m;
            if(t <= x) l = m + 1;
            else r = m;
        }
        return l - 1;
    }
};
```
Newton's iterative
```cpp
class Solution {
public:
    int mySqrt(int x) {
        long long r(x);
        while(r * r > x)
        {
            r = (r + x / r) >> 1;
        }
        return r;
    }
};
```