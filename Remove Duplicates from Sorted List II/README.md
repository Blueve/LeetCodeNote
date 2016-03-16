Remove Duplicates from Sorted List II
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
        ListNode h(0);
        h.next = head;
        ListNode *pre = &h, *cur = head;
        int del;
        while(cur)
        {
            if(cur->next && cur->val == cur->next->val)
            {
                while(cur->next && cur->val == cur->next->val)
                {
                    cur = cur->next;
                }
                pre->next = cur->next;
                cur = pre;
            }
            pre = cur;
            cur = cur->next;
        }
        return h.next;
    }
};
```
