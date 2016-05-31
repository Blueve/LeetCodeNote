Substring with Concatenation of All Words
==========

## C++


```cpp
class Solution {
public:
    vector<int> findSubstring(string s, vector<string>& words) {
        int n = words.size(), len = words[0].length();
        vector<int> result;
        
        unordered_map<string, int> count;
        for(auto& word : words)
            ++count[word];
        
        for(int i(0); i < s.length() - n * len + 1; ++i)
        {
            unordered_map<string, int> cur;
            int j = 0;
            for(; j < n; ++j)
            {
                auto word = s.substr(i + j * len, len);
                if(count.count(word) && ++cur[word] <= count[word])
                    continue;
                else
                    break;
            }
            if(j == n)
                result.push_back(i);
        }
        return result;
    }
};
```
