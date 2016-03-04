Populating Next Right Pointers in Each Node
==========

## C++


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
        if(root == NULL) return;
        
        queue<TreeLinkNode*> bfs;
        queue<int> bfsD;
        
        TreeLinkNode *node(NULL), *preN;
        int depth, preD(0);
        
        bfs.push(root);
        bfsD.push(0);
        while(!bfs.empty())
        {
            preN = node;
            node = bfs.front();
            
            preD = depth;
            depth = bfsD.front();
            bfs.pop(); bfsD.pop();
            
            if(preN)
            {
                preN->next = depth == preD ? node : NULL;
            }
            
            
            if(node->left)
            {
                bfs.push(node->left);
                bfsD.push(depth + 1);
            }
            if(node->right) 
            {
                bfs.push(node->right);
                bfsD.push(depth + 1);
            }
        }
    }
};
```
Better
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
        if(root == NULL) return;
        
        TreeLinkNode *cur, *pre(root);
        while(pre->left)
        {
            cur = pre;
            while(cur)
            {
                cur->left->next = cur->right;
                if(cur->next) cur->right->next = cur->next->left;
                cur = cur->next;
            }
            pre = pre->left;
        }
    }
};
```
