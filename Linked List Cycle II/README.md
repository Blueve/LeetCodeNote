Linked List Cycle II
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
    ListNode *detectCycle(ListNode *head) {
        // Find a node in the cycle
        ListNode *slow, *fast, *node = NULL;
        slow = fast = head;
        while(fast && fast->next && fast->next->next)
        {
            slow = slow->next;
            fast = fast->next->next;
            if(slow == fast)
            {
                node = slow;
                break;
            }
        }
        if(!node) return NULL;
        // Slow and fast pointer run together(by same speed)
        slow = head; fast = node->next;
        while(slow != fast)
        {
            fast = (fast == node ? head : fast->next);
            slow = slow->next;
        }
        return slow;
    }
};
```
