Integer Break
==========

## C++


```cpp
class Solution {
public:
    int integerBreak(int n) {
        static unordered_map<int, int> DP;
        DP[2] = 1; DP[3] = 2; DP[4] = 4;
        DP[5] = 6; DP[6] = 9; DP[7] = 12;
        
        return DP[n] ? DP[n] : 3 * integerBreak(n - 3);
    }
};
```
