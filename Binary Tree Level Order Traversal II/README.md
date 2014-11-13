Binary Tree Level Order Traversal II
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
      vector<vector<int> > levelOrderBottom(TreeNode *root) {
          stack<vector<int>> result;
          vector<vector<int>> ret;
          
          vector<int> line;
          if(root == NULL) return ret;
          
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
                  result.push(line);
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
          result.push(line);
          
          
          while(!result.empty())
          {
              ret.push_back(result.top());
              result.pop();
          }
          return ret;
      }
  };
  ```