Binary Tree Zigzag Level Order Traversal
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
    vector<vector<int>> zigzagLevelOrder(TreeNode* root) {
        vector<vector<int>> result;
        if(!root) return result;
        
        queue<TreeNode*> bfs;
        bfs.push(root);
        bool flag(true);
        while(!bfs.empty())
        {
            int N = bfs.size();
            vector<int> line(N);
            for(int i(0); i < N; ++i)
            {
                auto node = bfs.front();
                bfs.pop();
                
                flag ? line[i] = node->val : line[N - i - 1] = node->val;

                if(node->left) bfs.push(node->left);
                if(node->right)bfs.push(node->right);
            }
            flag = !flag;
            result.push_back(line);
        }
    }
};
```
