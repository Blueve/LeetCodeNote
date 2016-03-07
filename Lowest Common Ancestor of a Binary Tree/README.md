Lowest Common Ancestor of a Binary Tree
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
    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
        if(!root || root == p || root == q) return root;
        
        // Find in left
        auto l = lowestCommonAncestor(root->left, p, q);
        // Find in right
        auto r = lowestCommonAncestor(root->right, p, q);
        
        // Found p/q both left and right
        if(l && r) return root;
        else if(!l) return r;
        else return l;
    }
};
```
