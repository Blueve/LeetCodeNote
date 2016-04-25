Sort List
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
    ListNode* sortList(ListNode* head)
    {
        if (!head || !head->next) return head;
        // Find mid node
        ListNode *pre = NULL, *mid, *fast;
        mid = fast = head;
        while (fast && fast->next)
        {
            pre = mid;
            mid = mid->next;
            fast = fast->next->next;
        }
        // Cut off
        pre->next = NULL;
        // Sort
        auto l1 = sortList(head);
        auto l2 = sortList(mid);
        // Merge
        return merge(l1, l2);
    }

    ListNode* merge(ListNode* h1, ListNode* h2)
    {
        ListNode h(0), *cur, *l1 = h1, *l2 = h2;
        cur = &h;
        while (l1 && l2)
        {
            if (l1->val < l2->val)
            {
                cur->next = l1;
                l1 = l1->next;
            }
            else
            {
                cur->next = l2;
                l2 = l2->next;
            }
            cur = cur->next;
        }
        while (l1)
        {
            cur->next = l1;
            l1 = l1->next;
            cur = cur->next;
        }
        while (l2)
        {
            cur->next = l2;
            l2 = l2->next;
            cur = cur->next;
        }
        cur->next = NULL;
        return h.next;
    }
};
```
