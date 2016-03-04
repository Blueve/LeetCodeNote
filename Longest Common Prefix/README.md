Longest Common Prefix
==========

## C++

Count prefix positional
```cpp
class Solution {
public:
    string longestCommonPrefix(vector<string>& strs) {
        int N(strs.size()), n;
        if(!N) return "";
        
        n = strs[0].size();
        for(int p(0); p < n ; ++p)
        {
            char ch = strs[0][p];
            for(int i(1); i < N; ++i)
            {
                if(strs[i].size() == p || strs[i][p] != ch)
                    return strs[i].substr(0, p);
            }
        }
        return strs[0];
    }
};
```
Reduce prefix one by one
```cpp
class Solution {
public:
    string longestCommonPrefix(vector<string>& strs) {
        int N(strs.size());
        if(!N) return "";
        
        int prefix(strs[0].length()), j, strLen;
        
        for(int i(1); i < N; i++)
        {
            strLen = strs[i].length();
            for(j = 0; j < strLen && j < prefix; j++)
            {
                if(strs[i][j] != strs[0][j]) break;
            }
            prefix = j;
        }
        return strs[0].substr(0,prefix);
    }
};
```
