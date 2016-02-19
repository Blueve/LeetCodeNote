Binary Tree Paths
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
      vector<string> binaryTreePaths(TreeNode* root) {
          vector<string> result;
          
          if(!root) return result;
          
          _binaryTreePaths(root, "", result);
          return result;
      }
      
      void _binaryTreePaths(TreeNode* root, string path, vector<string>& result)
      {
          path += to_string(root->val);
          if(!root->left && !root->right)
          {
              result.push_back(path);
              return;
          }
          if(root->left)  _binaryTreePaths(root->left,  path + "->", result);
          if(root->right) _binaryTreePaths(root->right, path + "->", result);
      }
  };
  ```