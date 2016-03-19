Populating Next Right Pointers in Each Node II
==========

## C++

BFS, O(N) Space
```cpp
/**
 * Definition for binary tree with next pointer.
 * struct TreeLinkNode {
 *  int val;
 *  TreeLinkNode *left, *right, *next;
 *  TreeLinkNode(int x) : val(x), left(NULL), right(NULL), next(NULL) {}
 * };
 */
class Solution {
public:
    void connect(TreeLinkNode *root) {
        if(!root) return;
        queue<TreeLinkNode*> bfs;
        TreeLinkNode *node, *pre;
        bfs.push(root);
        while(!bfs.empty())
        {
            pre = bfs.front(); bfs.pop();
            int n = bfs.size();
            if(pre->left) bfs.push(pre->left);
            if(pre->right)bfs.push(pre->right);
            while(n--)
            {
                node = bfs.front(); bfs.pop();
                pre->next = node;
                pre = node;
                
                if(node->left) bfs.push(node->left);
                if(node->right)bfs.push(node->right);
            }
            pre->next = NULL;
        }
    }
};
```
BFS, O(1) Space, using Link instead of queue
```cpp
/**
 * Definition for binary tree with next pointer.
 * struct TreeLinkNode {
 *  int val;
 *  TreeLinkNode *left, *right, *next;
 *  TreeLinkNode(int x) : val(x), left(NULL), right(NULL), next(NULL) {}
 * };
 */
class Solution {
public:
    void connect(TreeLinkNode *root) {
        if(!root) return;
        queue<TreeLinkNode*> bfs;
        TreeLinkNode *node, *pre;
        bfs.push(root);
        while(!bfs.empty())
        {
            pre = bfs.front(); bfs.pop();
            int n = bfs.size();
            if(pre->left) bfs.push(pre->left);
            if(pre->right)bfs.push(pre->right);
            while(n--)
            {
                node = bfs.front(); bfs.pop();
                pre->next = node;
                pre = node;
                
                if(node->left) bfs.push(node->left);
                if(node->right)bfs.push(node->right);
            }
            pre->next = NULL;
        }
    }
};
```
