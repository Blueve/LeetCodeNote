Repeated DNA Sequences
==========

## C++


```cpp
class Solution {
public:
    vector<string> findRepeatedDnaSequences(string s) {
        unordered_map<string, int> m;
        int len = s.length() - 10;
        for(int i(0); i <= len; ++i)
            m[s.substr(i, 10)]++;
        
        vector<string> result;
        for(auto &item : m)
            if(item.second > 1) result.push_back(item.first);
        
        return result;
    }
};
```
