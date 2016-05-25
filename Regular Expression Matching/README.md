Regular Expression Matching
==========

## C++


```cpp
class Solution {
public:
    bool isMatch(string s, string p) {
        vector<vector<bool>> visit(s.length() + 1, vector<bool>(p.length() + 1));
        return dfs(s, p, 0, 0, visit);
    }
    
    bool dfs(string& s, string& p, int i, int j, vector<vector<bool>>& visit)
    {
        if(visit[i][j]) return false;
        visit[i][j] = true;
        
        if(j == p.length() && i == s.length())
            return true;
            
        bool result = false;
        if(i < s.length() && (s[i] == p[j] || p[j] == '.'))
        {
            if(j < p.length() - 1 && p[j + 1] == '*')
                result = dfs(s, p, i + 1, j + 2, visit) || dfs(s, p, i + 1, j, visit) || dfs(s, p, i, j + 2, visit);
            else
                result = dfs(s, p, i + 1, j + 1, visit);
        }
        else if(j < p.length() - 1 && p[j + 1] == '*')
        {
            result = dfs(s, p, i, j + 2, visit);
        }
        return result;
    }
};
```
