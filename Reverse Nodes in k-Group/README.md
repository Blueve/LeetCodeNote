Reverse Nodes in k-Group
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
    ListNode* reverseKGroup(ListNode* head, int k) {
        if (!k || !head) return head;

        ListNode *pre = NULL, *cur = head, *next, *end, *h = head, *ph = NULL;
        do
        {
            // Find reverse tail
            end = cur;
            for (int i(1); end && i < k; ++i)
                end = end->next;
            // Link to pre list tail
            if(end && !ph)
                h = end;
            else if(!end)
            {
                if(ph) ph->next = cur;
                break;
            }
            else if(ph)
                ph->next = end;
            end = end->next;

            // Reverse 
            ph = cur;
            while (cur != end)
            {
                next = cur->next;
                cur->next = pre;
                pre = cur;
                cur = next;
            }
            pre = NULL;
        } while (cur);
        return h;
    }
};
```
