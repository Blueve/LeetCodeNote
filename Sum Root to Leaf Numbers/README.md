Sum Root to Leaf Numbers
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
      int sumNumbers(TreeNode* root) {
          return _sumNumbers(root, 0);
      }
      
      int _sumNumbers(TreeNode* root, int s)
      {
          if(!root) return 0;
          
          s *= 10;
          s += root->val;
          
          if(!root->left && !root->right) return s;
          
          int l = _sumNumbers(root->left, s);
          int r = _sumNumbers(root->right, s);
          
          return l + r;
      }
  };
  ```