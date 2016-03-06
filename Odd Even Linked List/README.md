Odd Even Linked List
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
    ListNode* oddEvenList(ListNode* head) {
        if(!head) return NULL;
        
        int i(0);
        ListNode *pre = head, *next = head->next, *even, *tmp;
        even = new ListNode(0);
        tmp = even; 
        while(next)
        {
            if(!(i & 1)) // Even
            {
                tmp->next = next;
                pre->next = next->next;
                tmp = tmp->next;
            }
            else
            {
                pre = pre->next;
            }
            next = next->next;
            ++i;
        }
        tmp->next = NULL;
        pre->next = even->next;
        return head;
    }
};
```
Better
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
    ListNode* oddEvenList(ListNode* head) {
        if(!head || !head->next) return head;
        ListNode *odd = head, *even = head->next;
        ListNode *evenH = even;
        while(even && even->next)
        {
            odd->next  = odd->next->next;
            even->next = even->next->next;
            odd  = odd->next;
            even = even->next;
        }
        odd->next = evenH;
        return head;
    }
};
```
