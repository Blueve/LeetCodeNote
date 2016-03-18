Binary Tree Postorder Traversal
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
    vector<int> postorderTraversal(TreeNode* root) {
        vector<int> result;
        if(!root) return result;
        stack<TreeNode*> dfs;
        TreeNode *node;
        dfs.push(root);
        while(!dfs.empty())
        {
            node = dfs.top();
            dfs.pop();
            
            result.push_back(node->val);
            
            if(node->left) dfs.push(node->left);
            if(node->right)dfs.push(node->right);
        }
        reverse(result.begin(), result.end());
        return result;
    }
};
```
