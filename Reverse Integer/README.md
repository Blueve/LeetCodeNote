Reverse Integer
==========

## C++

Handle overflow by 64bit integer
```cpp
class Solution {
public:
    int reverse(int x) {
        long long r(0);
        
        while(x)
        {
            r *= 10;
            r += x % 10;
            x /= 10;
        }
        if(r > INT_MAX || r < INT_MIN) return 0;
        return r;
    }
};
```
Handle overflow by inner check
```cpp
class Solution {
public:
    int reverse(int x) {
        const int MIN(INT_MIN / 10), MAX(INT_MAX / 10);
        int r(0);
        
        while(x)
        {
            if(r > MAX || r < MIN) return 0;
            r *= 10;
            r += x % 10;
            x /= 10;
        }
        return r;
    }
};
```
