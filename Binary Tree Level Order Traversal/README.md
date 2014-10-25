Binary Tree Level Order Traversal
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
      vector<vector<int> > levelOrder(TreeNode *root) {
          vector<vector<int>> result;
          vector<int> line;
          if(root == NULL) return result;
          
          queue<TreeNode *> bfs;
          queue<int>        depth;
          bfs.push(root);
          depth.push(0);
          
          TreeNode* node;
          int d;
          int pre(0);
          while(!bfs.empty())
          {
              node = bfs.front();
              bfs.pop();
              
              d = depth.front();
              depth.pop();
              
              if(d != pre)
              {
                  result.push_back(line);
                  line.clear();
              }
              line.push_back(node->val);
              pre = d;
              
              if(node->left != NULL)
              {
                  bfs.push(node->left);
                  depth.push(d + 1);
              }
              if(node->right != NULL)
              {
                  bfs.push(node->right);
                  depth.push(d + 1);
              }
          }
          result.push_back(line);
          return result;
      }
  };
  ```