Recover Binary Search Tree
==========

## C++

O(N) Space
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
    void recoverTree(TreeNode* root) {
        if(!root) return;
        
        stack<TreeNode*> dfs;
        TreeNode *node = root, *pre = NULL, *A = NULL, *B = NULL;
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
                if(pre && !A && node->val < pre->val)
                {
                    A = pre;
                    B = node;
                }
                else if(B && node->val < B->val)
                {
                    B = node;
                }
                pre = node;
                node = node->right;
            }
        }
        swap(A->val, B->val);
    }
};
```

O(1) Space, Morris traversal
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
    void recoverTree(TreeNode* root) {
        if(!root) return;
        
        TreeNode *node = root, *pre = NULL, *A = NULL, *B = NULL;
        while(node)
        {
            // Find node's pre-node
            // If it is leaf node, make it right link to node
            // else make it right NULL cause visited before.
            if(node->left)
            {
                auto p = node->left;
                while(p->right && p->right != node)
                    p = p->right;
                if(!p->right)
                {
                    p->right = node;
                    node = node->left;
                    continue;
                }
                else
                    p->right = NULL;
            }
            if(pre && !A && node->val < pre->val)
            {
                A = pre;
                B = node;
            }
            else if(B && node->val < B->val)
            {
                B = node;
            }
            pre = node;
            node = node->right;
        }
        swap(A->val, B->val);
    }
};
```
