Reverse Linked List II
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
    ListNode* reverseBetween(ListNode* head, int m, int n) {
        int i(0);
        ListNode h(0);
        h.next = head;
        ListNode *pre = &h, *cur, *start, *tmp;
        
        for(; i < m - 1; ++i)
            pre = pre->next;
        cur = pre->next;
        for(++i; i < n; ++i)
        {
            auto next = cur->next;
            cur->next = next->next;
            next->next = pre->next;
            pre->next = next;
        }
        return h.next;
    }
};
```
