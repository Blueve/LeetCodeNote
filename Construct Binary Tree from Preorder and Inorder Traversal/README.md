Construct Binary Tree from Preorder and Inorder Traversal
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
    TreeNode* buildTree(vector<int>& preorder, vector<int>& inorder) {
        int N(preorder.size());
        int i(N - 1), j(N - 1);
        TreeNode* cur = NULL;
        stack<TreeNode*> stk;
        while(i >= 0)
        {
            if(!stk.empty() && stk.top()->val == preorder[i])
            {
                stk.top()->left = cur;
                cur = stk.top();
                stk.pop();
                --i;
            }
            else
            {
                auto node = new TreeNode(inorder[j]);
                node->right = cur;
                cur = NULL;
                stk.push(node);
                --j;
            }
        }
        return cur;
    }
};
```
