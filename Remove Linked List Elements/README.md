Remove Linked List Elements
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
    ListNode* removeElements(ListNode* head, int val) {
        ListNode *h = new ListNode(0);
        h->next = head;
        ListNode *pre = h, *node = head, *result;
        while(node)
        {
            if(node->val == val)
            {
                pre->next = node->next;
                delete node;
                node = pre->next;
            }
            else
            {
                pre = node;
                node = node->next;
            }
        }
        result = h->next;
        delete h;
        return result;
    }
};
```
