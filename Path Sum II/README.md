Path Sum II
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
    vector<vector<int>> pathSum(TreeNode* root, int sum) {
        vector<vector<int>> result;
        vector<int> path;
        _pathSum(root, sum, result, path);
        return result;
    }
    
    void _pathSum(TreeNode* root, int sum, vector<vector<int>>& result, vector<int>& path)
    {
        if(!root) return;
        path.push_back(root->val);
        // If root is leaf node, check sum
        if(!root->left && !root->right && sum == root->val)
            result.push_back(path);
        else
        {
            _pathSum(root->left, sum - root->val, result, path);
            _pathSum(root->right, sum - root->val, result, path);
        }
        path.pop_back();
    }
};
```
