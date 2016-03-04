Minimum Depth of Binary Tree
==========

## C++

BFS with two queue
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
    int minDepth(TreeNode* root) {
        if(!root) return 0;
        
        queue<int> d;
        queue<TreeNode*> bfs;
        int depth;
        TreeNode* node;
        
        d.push(1);
        bfs.push(root);
        while(!bfs.empty())
        {
            depth = d.front();
            node = bfs.front();
            d.pop();
            bfs.pop();
            
            if(!node->left && !node->right) return depth;
            
            if(node->left)
            {
                d.push(depth + 1);
                bfs.push(node->left);
            }
            if(node->right)
            {
                d.push(depth + 1);
                bfs.push(node->right);
            }
        }
    }
};
```

BFS with one queue
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
    int minDepth(TreeNode* root) {
        if(!root) return 0;
        
        queue<TreeNode*> bfs;
        TreeNode* node;
        int depth(0), N;
        
        bfs.push(root);
        while(!bfs.empty())
        {
            ++depth;
            
            N = bfs.size();
            for(int i(0); i < N; ++i)
            {
                node = bfs.front();
                bfs.pop();
                
                if(!node->left && !node->right) return depth;
            
                if(node->left)  bfs.push(node->left);
                if(node->right) bfs.push(node->right);
            }
        }
    }
};
```

DFS
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
    int minDepth(TreeNode* root) {
        if(!root) return 0;
        if(root->left && root->right)
            return min(minDepth(root->left), minDepth(root->right)) + 1;
        else
            return max(minDepth(root->left), minDepth(root->right)) + 1;
    }
};
```
