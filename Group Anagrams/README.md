Group Anagrams
==========

## C++

O(NlogN) + O(N)
```cpp
class Solution {
    string hashFunc(string str)
    {
        sort(str.begin(), str.end());
        return str;
    }
    
public:
    vector<vector<string>> groupAnagrams(vector<string>& strs) {
        vector<vector<string>> result;
        // Build hash table
        unordered_map<string, multiset<string>> hash;
        for(auto s : strs)
        {
            hash[hashFunc(s)].insert(s);
        }
        // Arrange result
        for(auto item : hash)
        {
            result.push_back(vector<string>(item.second.begin(), item.second.end()));
        }
        return result;
    }
};
```
O(N) + O(N)
```cpp
class Solution {
    string hashFunc(const string& str)
    {
        short counter[26] = {0};
        for(auto c : str)
            ++counter[c - 'a'];
        
        string h(str.size(), 'a');
        int p(0);
        for(int i(0); i < 26; ++i)
            while(counter[i] --> 0)
                h[p++] += i;
        
        return h;
    }
    
public:
    vector<vector<string>> groupAnagrams(vector<string>& strs) {
        vector<vector<string>> result;
        // Build hash table
        unordered_map<string, multiset<string>> hash;
        for(auto s : strs)
        {
            hash[hashFunc(s)].insert(s);
        }
        // Arrange result
        for(auto item : hash)
        {
            result.push_back(vector<string>(item.second.begin(), item.second.end()));
        }
        return result;
    }
};
```