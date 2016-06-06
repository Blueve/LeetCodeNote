Shortest Palindrome
==========

## C++

Using KMP to find the prefix
```cpp
class Solution {
public:
    string shortestPalindrome(string s) {
        if(s.empty()) return "";
        
        string t = s;
        reverse(t.begin(), t.end());
        string u = s + '|' + t;
        
        vector<int> p((s.length() << 1) + 1);
        for(int i(1); i < p.size(); ++i)
        {
            while(j > 0 && u[i] != u[j])
                j = p[j - 1];
                
            p[i] = u[i] == u[j] ? ++j : j;
        }
        return t.substr(0, s.length() - p.back()) + s;
    }
};
```
