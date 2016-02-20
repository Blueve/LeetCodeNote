Binary Tree Level Order Traversal
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
      vector<vector<int>> levelOrder(TreeNode* root) {
          vector<vector<int>> result;
          vector<int> level;
          if(!root) return result;
          
          queue<TreeNode*> bfs;
          TreeNode* node;
          
          bfs.push(root);
          while(!bfs.empty())
          {
              int N(bfs.size());
              level.clear();
              for(int i(0); i < N; ++i)
              {
                  node = bfs.front();
                  bfs.pop();
                  
                  level.push_back(node->val);
                  
                  if(node->left) bfs.push(node->left);
                  if(node->right) bfs.push(node->right);
              }
              result.push_back(level);
          }
          return result;
      }
  };
  ```