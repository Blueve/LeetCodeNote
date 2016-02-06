Convert Sorted Array to Binary Search Tree
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
      TreeNode* sortedArrayToBST(vector<int>& nums) {
          return create(nums, 0, nums.size());
      }
      
      TreeNode* create(vector<int>& nums, int left, int right)
      {
          if(right <= left) return NULL;
          
          int mid = (right - left) / 2 + left;
          TreeNode* root = new TreeNode(nums[mid]);
          root->left = create(nums, left, mid);
          root->right = create(nums, mid + 1, right);
          return root;
      }
  };
  ```