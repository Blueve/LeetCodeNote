Isomorphic Strings
==========

## C++


```cpp
class Solution {
public:
    bool isIsomorphic(string s, string t) {
        unordered_map<char, char> mapA, mapB;
        int len(s.size());
        for(int i(0); i < len; ++i)
        {
            if(mapA.count(s[i]))
            {
                if(mapA[s[i]] != t[i]) return false;
            }
            else if(mapB.count(t[i]))
            {
                if(mapB[t[i]] != s[i]) return false;
            }
            else
            {
                mapA[s[i]] = t[i];
                mapB[t[i]] = s[i];
            }
        }
        return true;
    }
};
```
Better
```cpp
class Solution {
public:
    bool isIsomorphic(string s, string t) {
        int mapA[128] = {0}, mapB[128] = {0};
        int len(s.size());
        for(int i(0); i < len; ++i)
        {
            if(mapA[s[i]] != mapB[t[i]]) return false;
            else mapA[s[i]] = mapB[t[i]] = i + 1;
        }
        return true;
    }
}; 
```
