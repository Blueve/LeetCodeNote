Reverse Words in a String
==========

## C++


```cpp
class Solution {
public:
    void reverseWords(string &s) {
        int len = s.length();
        if (!len) return;

        int p1 = 0, p2 = 0, start;
        while (p2 < len)
        {
            // Skip space
            while (p2 < len && s[p2] == ' ')
                p2++;
            
            // There is no word below  
            if(p2 == len) break;
            if(p1) p1++;
            
            // Read a word
            start = p2;
            while (p2 < len && s[p2] != ' ')
                p2++;
            
            // Move and reverse word to front
            for (int i(p2 - 1); i >= start && i > p1; --i)
                swap(s[p1++], s[i]);
            
            // Handle p1
            while (p1 < len && s[p1] != ' ')
                p1++;
        }
        s.erase(s.begin() + p1, s.end());
        reverse(s.begin(), s.end());
    }
};
```
