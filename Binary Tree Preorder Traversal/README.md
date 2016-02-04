Binary Tree Preorder Traversal
==========

## C++

  - Answer

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
      vector<int> preorderTraversal(TreeNode* root) {
          vector<int> result;
          _preorderTraversal(root, result);
          return result;
      }
      
      void _preorderTraversal(TreeNode* root, vector<int>& result)
      {
          if(!root) return;
          result.push_back(root->val);
          _preorderTraversal(root->left, result);
          _preorderTraversal(root->right, result);
      }
  };
  ```
  Iteratively
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
      vector<int> preorderTraversal(TreeNode* root) {
          vector<int> result;
          if(!root) return result;
          
          stack<TreeNode*> dfs;
          TreeNode* node;
          dfs.push(root);
          while(!dfs.empty())
          {
              node = dfs.top();
              dfs.pop();
              
              result.push_back(node->val);
              
              if(node->right) dfs.push(node->right);
              if(node->left) dfs.push(node->left);
          }
          return result;
      }
  };
  ```