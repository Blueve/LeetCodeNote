Binary Tree Inorder Traversal
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
    vector<int> inorderTraversal(TreeNode* root) {
        vector<int> result;
        _inorderTraversal(root, result);
        return result;
    }
    
    void _inorderTraversal(TreeNode* root, vector<int>& result)
    {
        if(!root) return;
        _inorderTraversal(root->left, result);
        result.push_back(root->val);
        _inorderTraversal(root->right, result);
    }
};
```

Iteratively
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
    vector<int> inorderTraversal(TreeNode* root) {
        vector<int> result;
        
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
                result.push_back(node->val);
                node = node->right;
            }
        }
        return result;
    }
};
```
