Construct Binary Tree from Inorder and Postorder Traversal
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
    TreeNode* buildTree(vector<int>& inorder, vector<int>& postorder) {
        int N(inorder.size()), i(0), j(0);
        stack<TreeNode*> stk;
        // Built Tree's root
        TreeNode* cur = NULL;
        while(j < N)
        {
            // Inorder: left * right
            // Postorder: left right *
            // Then the node which in the inorder list' front
            // must be the parent of postorder's front
            
            // When postorder meet stack's top and equal with it,
            // then means cur is the right part of stack's top.
            if(!stk.empty() && stk.top()->val == postorder[j])
            {
                stk.top()->right = cur;
                cur = stk.top();
                stk.pop();
                ++j;
            }
            // Else, cur is the left part of inorder's front
            else
            {
                auto node = new TreeNode(inorder[i]);
                node->left = cur;
                cur = NULL;
                stk.push(node);
                ++i;
            }
        }
        return cur;
    }
};
```
