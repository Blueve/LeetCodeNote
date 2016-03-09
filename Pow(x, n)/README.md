Pow(x, n)
==========

## C++


```cpp
class Solution {
public:
    double myPow(double x, int n) {
        if(n == 0) return 1;
        else if(n == 1) return x;
        else if(n == -1) return 1/x;
        
        return myPow(x*x, n/2) * (n & 1 ? (n < 0 ? 1/x : x) : 1);
    }
};
```

```cpp
class Solution {
public:
    double myPow(double x, int n) {
        if(n == 0) return 1;
        else if(n == 1) return x;
        else if(n < 0) return myPow(1/x, -n);
        
        return myPow(x*x, n/2) * (n & 1 ? x : 1);
    }
};
```
