Decode Ways
==========

## C++

O(N) Time, O(N) Space
```cpp
class Solution {
public:
    int numDecodings(string s) {
        auto len = s.length();
        if(len == 0) return 0;
        vector<int> DP(len + 1);
        DP[0] = 1;
        DP[1] = s[0] == '0' ? 0 : 1;
        for(int i(1); i < len; ++i)
        {
            if(s[i] != '0')
                DP[i + 1] = DP[i];
            
            if(s[i - 1] == '1' || (s[i - 1] == '2' && s[i] <= '6'))
                DP[i + 1] += DP[i - 1];
        }
        return DP[len];
    }
};
```

O(N) Time, O(1) Space
```cpp
class Solution {
public:
    int numDecodings(string s) {
        auto len = s.length();
        if(len == 0) return 0;
        
        int next, cur = (s[0] == '0' ? 0 : 1), pre = 1;
        for(int i(1); i < len; ++i)
        {
            next = 0;
            if(s[i] != '0')
                next = cur;
            if(s[i - 1] == '1' || (s[i - 1] == '2' && s[i] <= '6'))
                next += pre;
                
            pre = cur;
            cur = next;
        }
        return cur;
    }
};
```
