Binary Search Tree Iterator
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
  class BSTIterator {
      stack<TreeNode*> dfs;
      TreeNode* node;
  public:
      BSTIterator(TreeNode *root) {
          node = root;
      }
  
      /** @return whether we have a next smallest number */
      bool hasNext() {
          return !dfs.empty() || node;
      }
  
      /** @return the next smallest number */
      int next() {
          do
          {
              if(node)
              {
                  dfs.push(node);
                  node = node->left;
              }
              else
              {
                  TreeNode *n = dfs.top();
                  dfs.pop();
                  node = n->right;
                  return n->val;
              }
          } while(!dfs.empty() || node);
      }
  };
  
  /**
   * Your BSTIterator will be called like this:
   * BSTIterator i = BSTIterator(root);
   * while (i.hasNext()) cout << i.next();
   */
  ```