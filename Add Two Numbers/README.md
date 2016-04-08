Add Two Numbers
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
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        int a, b, s, c = 0;
        ListNode h(0), *cur = &h;
        while(l1 || l2)
        {
            a = b = 0;
            if(l1)
            {
                a = l1->val;
                l1 = l1->next;
            }
            if(l2)
            {
                b = l2->val;
                l2 = l2->next;
            }
            s = a + b + c;
            if(s >= 10)
            {
                s -= 10;
                c = 1;
            }
            else c = 0;
            cur->next = new ListNode(s);
            cur = cur->next;
        }
        if(c) cur->next = new ListNode(1);
        return h.next;
    }
};
```
