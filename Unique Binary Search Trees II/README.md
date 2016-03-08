Single Number
==========

## C++


```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    vector<TreeNode*> generateTrees(int n) {
        return _subTrees(1, n);
    }
    
    vector<TreeNode*> _subTrees(int from, int to)
    {
        vector<TreeNode*> result;
        if(from > to)
        {
            result.push_back(NULL);
            return result;
        }
        for(int i(from); i <= to; ++i)
        {
            auto l = _subTrees(from, i - 1);
            auto r = _subTrees(i - 1, to);
            for(auto left : l)
            {
                for(auto right : r)
                {
                    auto root = new TreeNode(i);
                    root->left = left;
                    root->right = right;
                    result.push_back(root);
                }
            }
        }
        
    }
};
```
Static DP
```cpp
typedef unordered_map<int, unordered_map<int, vector<TreeNode*>>> Map;
 
class Solution {
public:
    vector<TreeNode*> generateTrees(int n) {
        if(!n) return vector<TreeNode*>();
        
        static Map DP;
        return _subTrees(1, n, DP);
    }
    
    vector<TreeNode*> _subTrees(int from, int to, Map& DP)
    {
        if(DP[from].count(to)) return DP[from][to];
        
        vector<TreeNode*> result;
        if(from > to)
        {
            // Handle if left/right tree is NULL
            result.push_back(NULL);
            return result;
        }
        // left root right
        // (1 2) [3] (4 5)
        for(int i(from); i <= to; ++i)
        {
            auto l = _subTrees(from, i - 1, DP);
            auto r = _subTrees(i + 1, to, DP);
            for(auto left : l)
            {
                for(auto right : r)
                {
                    auto root = new TreeNode(i);
                    root->left = left;
                    root->right = right;
                    result.push_back(root);
                }
            }
        }
        return DP[from][to] = result;
    }
};
```

Static DP and avoid vector's copy
```cpp
typedef unordered_map<int, unordered_map<int, vector<TreeNode*>*>> Map;
 
class Solution {
public:
    vector<TreeNode*> generateTrees(int n) {
        if(!n) return vector<TreeNode*>();
        
        static Map DP;
        return *_subTrees(1, n, DP);
    }
    
    vector<TreeNode*>* _subTrees(int from, int to, Map& DP)
    {
        if(DP[from].count(to)) return DP[from][to];
        
        vector<TreeNode*>* result = new vector<TreeNode*>();
        if(from > to)
        {
            // Handle if left/right tree is NULL
            result->push_back(NULL);
            return result;
        }
        // left root right
        // (1 2) [3] (4 5)
        for(int i(from); i <= to; ++i)
        {
            auto l = _subTrees(from, i - 1, DP);
            auto r = _subTrees(i + 1, to, DP);
            for(auto left(l->begin()); left != l->end(); ++left)
            {
                for(auto right(r->begin()); right != r->end(); ++right)
                {
                    auto root = new TreeNode(i);
                    root->left = *left;
                    root->right = *right;
                    result->push_back(root);
                }
            }
        }
        
        return DP[from][to] = result;
    }
};
```