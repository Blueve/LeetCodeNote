Clone Graph
==========

## C++


```cpp
/**
 * Definition for undirected graph.
 * struct UndirectedGraphNode {
 *     int label;
 *     vector<UndirectedGraphNode *> neighbors;
 *     UndirectedGraphNode(int x) : label(x) {};
 * };
 */
class Solution {
public:
    UndirectedGraphNode *cloneGraph(UndirectedGraphNode *node) {
        unordered_map<UndirectedGraphNode*, UndirectedGraphNode*> record;
        return node ? dfs(node, record) : NULL;
    }
    
    UndirectedGraphNode* dfs(
        UndirectedGraphNode *node, 
        unordered_map<UndirectedGraphNode*, UndirectedGraphNode*>& record)
    {
        if(record.count(node)) return record[node];
        UndirectedGraphNode *copy = new UndirectedGraphNode(node->label);
        record[node] = copy;
        for(auto &n : node->neighbors)
        {
            copy->neighbors.push_back(dfs(n, record));
        }
        return copy;
    }
};
```
