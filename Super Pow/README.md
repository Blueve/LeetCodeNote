Super Pow
==========

## C++


```cpp
class Solution {
public:
    int superPow(int a, vector<int>& b) {
        if(b.empty()) return 1;
        // a^(x*10 + y) => a^(x*10) * a^y
        int y = b.back();
        b.pop_back();
        return powMod(superPow(a, b), 10) * powMod(a, y) % 1337;
    }
    
    int powMod(int a, int n) {
        // a^b === (a % p)^b, note: '===' means lhs % p == rhs % p
        a %= 1337;
        int result = 1; // a^0 == 1
        for(int i = 0; i < n; ++i)
            result = (result * a) % 1337;
        return result;
    }
};
```
