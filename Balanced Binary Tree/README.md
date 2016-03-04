Balanced Binary Tree
==========

## C++


```cpp
/**
 * Definition for binary tree
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    bool isBalanced(TreeNode *root) {
        if(root == NULL) return true;
        int l = depth(root->left);
        int r = depth(root->right);
        if(abs(l - r) > 1) return false;
        else
        {
            return isBalanced(root->left) && isBalanced(root->right);
        }
    }
    
    int depth(TreeNode *root)
    {
        if(root == NULL)
            return 0;
        else
        {
            int l = depth(root->left);
            int r = depth(root->right);
            return l > r ? l + 1 : r + 1;
        }
    }
};
```
Another
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
    bool isBalanced(TreeNode* root) {
        return _isBalanced(root) + 1;
    }
    
    int _isBalanced(TreeNode* root)
    {
        if(root == NULL) return 0;
        
        int left = _isBalanced(root->left);
        int right = _isBalanced(root->right);
        
        if(abs(left - right) > 1 || left < 0 || right < 0) return -1;
        
        return max(left, right) + 1;
    }
};
```
