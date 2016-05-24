Interleaving String
==========

## C++


```cpp
class Solution {
public:
    bool isInterleave(string s1, string s2, string s3) {
        int l1 = s1.length(), l2 = s2.length(), l3 = s3.length();
        if(l1 + l2 != l3)
            return false;
        vector<vector<bool>> visited(l1 + 1, vector<bool>(l2 + 1));
        return dfs(s1, s2, s3, 0, 0, visited);
    }
    
    bool dfs(
        string& s1, string& s2, string& s3,
        int i, int j, vector<vector<bool>>& visited)
    {
        if(visited[i][j])
            return false;
        visited[i][j] = true;
        
        int k = i + j;
        return
            k == s3.length() ||
            i < s1.length() && s1[i] == s3[k] && dfs(s1, s2, s3, i + 1, j, visited) ||
            j < s2.length() && s2[j] == s3[k] && dfs(s1, s2, s3, i, j + 1, visited);
    }
};
```
