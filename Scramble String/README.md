Scramble String
==========

## C++

Purning
```cpp
class Solution {
    
public:
    bool isScramble(string s1, string s2) {
        if(s1 == s2)
            return true;
        
        int len = s1.length();
        
        // Ensure s1 and s2 are isomorphic
        int count[26] = {0};
        for(int i(0); i < len; ++i)
        {
            ++count[s1[i] - 'a'];
            --count[s2[i] - 'a'];
        }
        for(int i(0); i < 26; ++i)
        {
            if(count[i]) return false;
        }
        
        // Search sub part
        for(int i(1); i <= len - 1; ++i)
        {
            if(isScramble(s1.substr(0, i), s2.substr(0, i)) &&
               isScramble(s1.substr(i), s2.substr(i)) ||
               isScramble(s1.substr(0, i), s2.substr(len - i)) &&
               isScramble(s1.substr(i), s2.substr(0, len - i)))
               return true;
        }
        return false;
    }
};
```

Purning + DP, 
slower than purning only in LeetCode, but faster in below test case:

> "bcdebcdebcdebcdebcdebcdebcdebcdebcdebcdebcdebcdebcdebcdebcdebcdebcdebcdebcdebcdebcdebcde"
> "cebdcebdcebdcebdcebdcebdcebdcebdcebdcebdcebdcebdcebdcebdcebdcebdcebdcebdcebdcebdcebdcebd"

```cpp
class Solution {
    unordered_map<string, bool> DP;
public:
    bool isScramble(string s1, string s2) {
        string str = s1 + s2;
        auto it = DP.find(s1 + s2);
        if(it != DP.end())
            return it->second;
            
        if(s1 == s2)
            return DP[str] = true;
                
        int len = s1.length();
        
        // Ensure s1 and s2 are isomorphic
        int count[26] = {0};
        for(int i(0); i < len; ++i)
        {
            ++count[s1[i] - 'a'];
            --count[s2[i] - 'a'];
        }
        for(int i(0); i < 26; ++i)
        {
            if(count[i]) return DP[str] = false;
        }
        
        // Search sub part
        for(int i(1); i <= len - 1; ++i)
        {
            if(isScramble(s1.substr(0, i), s2.substr(0, i)) &&
               isScramble(s1.substr(i), s2.substr(i)) ||
               isScramble(s1.substr(0, i), s2.substr(len - i)) &&
               isScramble(s1.substr(i), s2.substr(0, len - i)))
               return DP[str] = true;
        }
        return DP[str] = false;
    }
};
```