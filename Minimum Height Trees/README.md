Minimum Height Trees
==========

## C++


```cpp
class Solution {
public:
    vector<int> findMinHeightTrees(int n, vector<pair<int, int>>& edges) {
        vector<set<int>> graph(n);
        for(auto p : edges)
        {
            graph[p.first].insert(p.second);
            graph[p.second].insert(p.first);
        }
        
        vector<int> leaf(n);
        int front(0), end(0);
        
        for(int i(0); i < n; ++i)
            if(graph[i].size() <= 1)
                leaf[end++] = i;
        
        while(front < n - 2)
        {
            int cur = end - front;
            for(int i(0); i < cur; ++i)
            {
                int node = leaf[front++];
                
                int j = *graph[node].begin();
                graph[j].erase(node);
                if(graph[j].size() == 1)
                    leaf[end++] = j;
            }
        }
        
        return vector<int>(leaf.begin() + front, leaf.end());
    }
};
```
