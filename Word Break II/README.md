Word Break II
==========

## C++


```cpp
class Solution {
public:
    vector<string> wordBreak(string s, unordered_set<string>& wordDict) {
        if(s.empty()) return {};
        unordered_map<int, vector<string>> DP;
        return wordBreak(s, wordDict, 0, DP);
    }
    
    vector<string> wordBreak(string& s, unordered_set<string>& wordDict, int start, unordered_map<int, vector<string>>& DP) {
        if(start == s.length()) return {""};
        
        auto iter = DP.begin();
        if((iter = DP.find(start)) != DP.end())
            return iter->second;
        
        vector<string> result;
        for(auto& word : wordDict)
        {
            auto len = word.length();
            if(start + len > s.length())
                continue;
            
            int i = 0;
            for(; i < len; ++i)
                if(s[start + i] != word[i])
                    break;
            
            if(i == len)
            {
                auto p = wordBreak(s, wordDict, start + len, DP);
                for(auto& item : p)
                    if(item.empty())
                        result.push_back(word);
                    else
                        result.push_back(word + ' ' + item);
            }
        }
        return DP[start] = result;
    }
};
```
