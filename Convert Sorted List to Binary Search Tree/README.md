Convert Sorted List to Binary Search Tree
==========

## C++


```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
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
    TreeNode* sortedListToBST(ListNode* head) {
        return buildTree(head, NULL);
    }
    
    TreeNode* buildTree(ListNode* start, ListNode* end)
    {
        if(start == end) return NULL;
        if(start->next == end) return new TreeNode(start->val);
        
        ListNode *slow = start, *fast = start->next;
        while(fast != end)
        {
            slow = slow->next;
            fast = fast->next;
            if(fast != end)
                fast = fast->next;
        }
        
        TreeNode *root = new TreeNode(slow->val);
        root->left = buildTree(start, slow);
        root->right = buildTree(slow->next, end);
        return root;
    }
};
```
