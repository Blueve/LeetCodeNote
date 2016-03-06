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
    ListNode *addTwoNumbers(ListNode *l1, ListNode *l2) {
        ListNode* result = new ListNode(0);
        ListNode* item  = result;
        ListNode* item1 = l1;
        ListNode* item2 = l2;
        
        while(true)
        {
            item->next = new ListNode(0);
            if(item1 != NULL)
                item->val += item1->val;
            if(item2 != NULL)
                item->val += item2->val;
            
            if(item->val >= 10)
            {
                item->val -= 10;
                item->next->val++;
            }
            
            if(item1 != NULL)
                item1 = item1->next;
            if(item2 != NULL)
                item2 = item2->next;
                
            if(item1 == NULL && item2 == NULL)
            {
                break;
            }
            item = item->next;
        }
        if(item->next->val == 0)
        {
            item->next = NULL;
        }
        
        return result;
    }
};
```
