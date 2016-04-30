Reverse Vowels of a String
==========

## C++


```cpp
class Solution {
public:
    string reverseVowels(string s) {
        bool Check[128] = {0};
        Check['a'] = Check['e'] = Check['i'] = Check['o'] = Check['u'] = 
        Check['A'] = Check['E'] = Check['I'] = Check['O'] = Check['U'] = true;
        int l = 0, r = s.length() - 1;
        while(l < r)
        {
            while(l < r && !Check[s[l]])
                ++l;
            while(l < r && !Check[s[r]])
                --r;
            swap(s[l++], s[r--]);
        }
        return s;
    }
};
```
