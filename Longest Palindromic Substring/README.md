Longest Palindromic Substring
==========

## C++


```cpp
class Solution {
public:
    string longestPalindrome(string s) {
        auto len = s.length();
        if(len < 2) return s;
        
        int l, m(0), p;
        int i, j;
        for(i = 0; i < len; ++i)
        {
            // s[i] is the middle
            l = 0;
            for(j = 0; i - j >= 0 && i + j < len; ++j)
            {
                if(s[i - j] != s[i + j]) break;
            }
            if(j--) l = j * 2 + 1;
            if(l > m) m = l, p = i - j;
            
            // s[i] & s[i + 1] are middle
            l = 0;
            for(j = 0; i - j >= 0 && i + j + 1 < len; ++j)
            {
                if(s[i - j] != s[i + j + 1]) break;
            }
            if(j--) l = j * 2 + 2;
            if(l > m) m = l, p = i - j;
        }
        return s.substr(p, m);
    }
};
```

Better
```cpp
class Solution {
public:
    string longestPalindrome(string s) {
        auto len = s.length();
        if(len < 2) return s;
        
        int p = 0, m = 0, l, r;
        for(int i = 0; i < len && len - i > m / 2;)
        {
            l = r = i;
            // Skip duplicate char
            while(r < len - 1 && s[r + 1] == s[r])
                ++r;
            i = r + 1;
            while(r < len - 1 && l > 0 && s[r + 1] == s[l - 1])
                ++r, --l;
            if(m < r - l + 1)
            {
                p = l;
                m = r - l + 1;
            }
        }
        return s.substr(p, m);
    }
};
```
