Flatten Binary Tree to Linked List
==========

## C++

  - Answer
  DFS, O(log(N)) Space
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
      void flatten(TreeNode* root) {
          if(!root) return;
          
          stack<TreeNode*> dfs;
          TreeNode *node, *pre = root;
          dfs.push(root);
          while(!dfs.empty())
          {
              node = dfs.top();
              dfs.pop();
              
              if(node->right)dfs.push(node->right);
              if(node->left) dfs.push(node->left);
              
              pre->right = node;
              pre->left = NULL;
              pre = pre->right;
          }
          pre->right = NULL;
      }
  };
  ```
  O(1) Space
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
      void flatten(TreeNode* root) {
          if(!root) return;
          
          stack<TreeNode*> dfs;
          TreeNode *node, *pre = root;
          dfs.push(root);
          while(!dfs.empty())
          {
              node = dfs.top();
              dfs.pop();
              
              if(node->right)dfs.push(node->right);
              if(node->left) dfs.push(node->left);
              
              pre->right = node;
              pre->left = NULL;
              pre = pre->right;
          }
          pre->right = NULL;
      }
  };
  ```