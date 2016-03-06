Remove Duplicates from Sorted List
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
class Solution {
public:
    ListNode* deleteDuplicates(ListNode* head) {
        if(!head) return NULL;
        ListNode *node = head->next, *pre = head;
        
        while(node)
        {
            if(node->val == pre->val)
            {
                pre->next = node->next;
                delete node;
                node = pre->next;
            }
            else
            {
                node = node->next;
                pre = pre->next;
            }
        }
        return head;
    }
};
```
