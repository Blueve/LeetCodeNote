Count Complete Tree Nodes
==========

## C++

O((LogN)^2)
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
    int countNodes(TreeNode* root) {
        TreeNode *left, *right;
        int l = 0, r = 0;
        left = right = root;
        // Get height of left and right
        while(left)
        {
            left = left->left;
            ++l;
        }
        while(right)
        {
            right = right->right;
            ++r;
        }
        // Equal means this root lead a perfect bintree
        if(l == r) return (1 << l - 1);
        // Else, count equals root + left part and right part
        return 1 + countNodes(root->left) + countNodes(root->right);
    }
};
```
