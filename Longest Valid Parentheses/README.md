Longest Valid Parentheses
==========

## C++


```cpp
class Solution {
public:
    int longestValidParentheses(string s) {
        int len = s.length();
        stack<int> stk;
        for(int i(0); i < len; ++i)
        {
            if(s[i] == '(')
                stk.push(i);
            else if(!stk.empty() && s[stk.top()] == '(')
                stk.pop();
            else
                stk.push(i);
        }
        if(stk.empty()) return len;
        
        int l, r = len, result = 0;
        while(!stk.empty())
        {
            l = stk.top();
            stk.pop();
            result = max(result, r - l - 1);
            r = l;
        }
        return max(result, r);
    }
};
```
