House Robber III
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
    int rob(TreeNode* root) {
        auto result = _rob(root);
        return max(result.first, result.second);
    }
    
    pair<int, int> _rob(TreeNode* root)
    {
        if(!root) return {0, 0};
        
        // first-> rob  second-> not rob
        auto l = _rob(root->left);
        auto r = _rob(root->right);
        
        int rob = root->val + l.second + r.second;
        int notrob = max(l.first, l.second) + max(r.first, r.second);
        
        return {rob, notrob};
    }
};
```
