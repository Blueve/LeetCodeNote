Binary Tree Level Order Traversal II
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
    vector<vector<int>> levelOrderBottom(TreeNode* root) {
        vector<vector<int>> result;
        vector<int> level;
        if(!root) return result;
        
        queue<TreeNode*> bfs;
        TreeNode* node;
        
        bfs.push(root);
        while(!bfs.empty())
        {
            int N(bfs.size());
            level.clear();
            for(int i(0); i < N; ++i)
            {
                node = bfs.front();
                bfs.pop();
                
                level.push_back(node->val);
                
                if(node->left) bfs.push(node->left);
                if(node->right) bfs.push(node->right);
            }
            result.push_back(level);
        }
        reverse(result.begin(), result.end());
        return result;
    }
};
```
Whitout reverse, but slower cause insert in front of vector
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
    vector<vector<int>> levelOrderBottom(TreeNode* root) {
        vector<vector<int>> result;
        _levelOrderBottom(root, 1, result);
        return result;
    }
    
    void _levelOrderBottom(TreeNode* root, int depth, vector<vector<int>>& result)
    {
        if(!root) return;
        if(depth > result.size()) result.insert(result.begin(), vector<int>());
        if(root->left) _levelOrderBottom(root->left, depth + 1, result);
        if(root->right) _levelOrderBottom(root->right, depth + 1, result);
        result[result.size() - depth].push_back(root->val);
    }
};
```
