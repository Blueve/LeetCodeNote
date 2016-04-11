Rotate List
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
    ListNode* rotateRight(ListNode* head, int k) {
        if(!head) return NULL;
        
        int n(1);
        ListNode *node, *fast;
        fast = head;
        while(fast->next)
        {
            fast = fast->next;
            ++n;
        }
        if(k %= n)
        {
            node = head;
            n -= k + 1;
            for(int i(0); i < n; ++i)
                node = node->next;
            fast->next = head;
            head = node->next;
            node->next = NULL;
        }
        return head;
    }
};
```
