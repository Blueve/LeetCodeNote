Binary Tree Maximum Path Sum
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
    int maxPathSum(TreeNode* root) {
        int m = INT_MIN;
        _maxPathSum(root, m);
        return m;
    }
    
    int _maxPathSum(TreeNode* root, int& m)
    {
        if(!root) return 0;
        
        // Make sure the path sum not less than 0
        int l = max(0, _maxPathSum(root->left, m));
        int r = max(0, _maxPathSum(root->right, m));
        
        // Check the sum across both left and right path
        m = max(m, l + r + root->val);
        
        // Return oneway max value
        return max(l, r) + root->val;
    }
};
```
