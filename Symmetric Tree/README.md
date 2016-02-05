Symmetric Tree
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
      bool isSymmetric(TreeNode* root) {
          if(root == NULL) return true;
          
          stack<TreeNode*> left, right;
          TreeNode *n1, *n2;
          
          left.push(root->left);
          right.push(root->right);
          
          while(!left.empty() && !right.empty())
          {
              n1 = left.top();
              n2 = right.top();
              left.pop(); right.pop();
              
              if(n1 == NULL && n2 == NULL) continue;
              if(n1 == NULL || n2 == NULL || n1->val != n2->val) return   false;
              
              left.push(n1->left);
              left.push(n1->right);
              
              right.push(n2->right);
              right.push(n2->left);
          }
          return true;
      }
  };
  ```