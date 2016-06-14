Wildcard Matching
==========

## C++


```cpp
class Solution {
public:
    bool isMatch(string s, string p) {
        vector<vector<bool>> visit(s.length() + 1, vector<bool>(p.length() + 1));
        return dfs(s, p, 0, 0, visit);
    }
    
    bool dfs(string& s, string& p, int i, int j, vector<vector<bool>>& visit) {
        if(visit[i][j]) return false;
        visit[i][j] = true;
        
        // Skip prefix
        while(i < s.length() && j < p.length() && (s[i] == p[j] || p[j] == '?'))
            ++i, ++j;
        if(i == s.length() && j == p.length())
            return true;
        
        // Match '*'
        if(j < p.length() && p[j] == '*')
        {
            for(int k = i; k <= s.length(); ++k)
            {
                if(dfs(s, p, k, j + 1, visit))
                    return true;
            }
        }
        return false;
    }
};
```

Better
```cpp
class Solution {
public:
    bool isMatch(string s, string p) {
        int i = 0, j = 0, match = 0, star = -1;
        while(i < s.length())
        {
            if(i < s.length() && j < p.length() && (s[i] == p[j] || p[j] == '?'))
                ++i, ++j;
            else if(j < p.length() && p[j] == '*')
            {
                star = j++;
                match = i;
            }
            else if(star != -1)
            {
                j = star + 1;
                i = ++match;
            }
            else
                return false;
        }
        
        while(j < p.length() && p[j] == '*')
            ++j;
        return j == p.length();
    }
};
```
