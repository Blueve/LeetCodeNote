Binary Tree Right Side View
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
      vector<int> rightSideView(TreeNode* root) {
          vector<int> result;
          dfs(root, 0, result);
          return result;
      }
      
      void dfs(TreeNode* root, int depth, vector<int>& result)
      {
          if(!root) return;
          
          if(result.size() == depth) result.push_back(root->val);
          else result[depth] = root->val;
          
          dfs(root->left, depth + 1, result);
          dfs(root->right, depth + 1, result);
      }
  };
  ```