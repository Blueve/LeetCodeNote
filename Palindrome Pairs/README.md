Palindrome Pairs
==========

## C++


```cpp
class Solution {
    
    bool isPalindrome(string& s) {
        int l = 0, r = s.length() - 1;
        while(l < r && s[l] == s[r])
            ++l, --r;
        return l >= r;
    }
    
public:
    vector<vector<int>> palindromePairs(vector<string>& words) {
        unordered_map<string, int> hash;
        vector<vector<int>> result;
        for(int i(0); i < words.size(); ++i)
            hash[words[i]] = i;
        for(int i(0); i < words.size(); ++i)
        {
            reverse(words[i].begin(), words[i].end());
            int len = words[i].length();
            for(int j(0); j <= len; ++j)
            {
                auto l = words[i].substr(0, j);
                auto r = words[i].substr(j);
                
                if(hash.count(l) && isPalindrome(r) && hash[l] != i && len > j)
                    result.push_back({hash[l], i});
                if(hash.count(r) && isPalindrome(l) && hash[r] != i)
                    result.push_back({i, hash[r]});
            }
        }
        return result;
    }
};
```
