Validate Binary Search Tree
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
    bool isValidBST(TreeNode* root) {
        return _isValidBST(root, -2147483649L, 2147483648L);
    }
    
    bool _isValidBST(TreeNode* root, long long min, long long max)
    {
        if(!root) return true;
        if(root->val <= min || root->val >= max)
            return false;
        return _isValidBST(root->left, min, root->val) && 
               _isValidBST(root->right, root->val, max);
    }
};
```
Using inorder traversal to verify
```cpp
class Solution {
public:
    bool isValidBST(TreeNode* root) {
        TreeNode* pre = NULL;
        return _isValidBST(root, pre);
    }
    
    bool _isValidBST(TreeNode* root, TreeNode* &pre)
    {
        if(!root) return true;
        
        if(!_isValidBST(root->left, pre)) return false;
        
        if(pre && root->val <= pre->val) return false;
        pre = root;
        
        return _isValidBST(root->right, pre);
    }
};
```
