Binary Tree Inorder Traversal
==========

## C++

  - Answer

  ```cpp
  /**
   * Definition for binary tree
   * struct TreeNode {
   *     int val;
   *     TreeNode *left;
   *     TreeNode *right;
   *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
   * };
   */
  class Solution {
  public:
      vector<int> inorderTraversal(TreeNode *root) {
          vector<int> result;
          
          stack<TreeNode *> dfs;
          TreeNode* node = root;
          while(!dfs.empty() || node != NULL)
          {
              if(node != NULL)
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