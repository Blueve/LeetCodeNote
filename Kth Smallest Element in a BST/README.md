Kth Smallest Element in a BST
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
    int kthSmallest(TreeNode* root, int k) {

        stack<TreeNode*> dfs;
        TreeNode* node = root;
        
        while(!dfs.empty() || node)
        {
            if(node)
            {
                dfs.push(node);
                node = node->left;
            }
            else
            {
                node = dfs.top();
                dfs.pop();
                if(--k == 0) return node->val;
                node = node->right;
            }
        }
    }
};
```
