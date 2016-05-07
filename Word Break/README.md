Word Break
==========

## C++

O(NM), N for length of s, M for length of all words in dict.
```cpp
class Solution {
public:
    bool wordBreak(string s, unordered_set<string>& wordDict) {
        map<int, bool> DP;
        return _wordBreak(s, wordDict, 0, DP);
    }
    
    bool _wordBreak(string& s, unordered_set<string>& wordDict, int start, map<int, bool>& DP)
    {
        auto slen = s.length() - start;
        if(DP[start])
            return false;
            
        DP[start] = true;
            
        if(s.length() == start)
            return true;
        
        for(auto& word : wordDict)
        {
            auto len = word.length();
            if(len > slen)
                continue;
                
            int i = 0;
            for(; i < len; ++i)
            {
                if(s[start + i] != word[i])
                    break;
            }
            if(i == len && _wordBreak(s, wordDict, len + start, DP))
                return true;
        }
        return false;
    }
};
```

O(N^2)
```cpp
class Solution {
public:
    bool wordBreak(string s, unordered_set<string>& wordDict) {
        auto slen = s.length();
        vector<bool> DP(slen + 1);
        DP[0] = true;
        for(int i(1); i <= slen; ++i)
        {
            for(int j(i - 1); j >= 0; --j)
            {
                if(DP[j] && wordDict.count(s.substr(j, i - j)))
                {
                    DP[i] = true;
                    break;
                }
            }
        }
        
        return DP[slen];
    }
};
```
