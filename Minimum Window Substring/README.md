Minimum Window Substring
==========

## C++


```cpp
class Solution {
public:
    string minWindow(string s, string t) {
        int t_count[128] = {0}, t_c[128] = {0};
        for(auto ch : t)
            t_c[ch] = ++t_count[ch];
        
        // Find left
        int t_len = t.length(), s_len = s.length();
        int l = 0;
        while(l < s_len && !t_c[s[l]])
            ++l;
        
        // Find min window
        int r = l, i = 0;
        int min_len = INT_MAX, min_l = l;
        while(r < s_len)
        {
            if(t_c[s[r]])
            {
                if(--t_count[s[r]] >= 0)
                    ++i;
            }
            while(t_count[s[l]] < 0)
            {
                ++t_count[s[l++]];
                while(!t_c[s[l]]) ++l;
            }
            ++r;
            if(i >= t_len && r - l < min_len)
            {
                min_l = l;
                min_len = r - l;
            }
        }
        // Check if not exist a window
        if(i < t_len) return "";
        
        return s.substr(min_l, min_len);
    }
};
```
