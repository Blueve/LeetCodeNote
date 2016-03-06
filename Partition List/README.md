Partition List
==========

## C++

Using one extra head
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
    ListNode* partition(ListNode* head, int x) {
        if(!head) return NULL;
        ListNode h(0);
        h.next = head;
        ListNode *cur = head, *pre = &h, *left = &h;
        while(cur)
        {
            if(cur->val < x)
            {
                if(cur == left->next)
                    left = cur;
                else
                {
                    pre->next = cur->next;
                    cur->next = left->next;
                    left->next = cur;
                    left = cur;
                    cur = pre;
                }
            }
            
            pre = cur;
            cur = cur->next;
        }
        return h.next;
    }
};
```
Using two extra head
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
    ListNode* partition(ListNode* head, int x) {
        if(!head) return NULL;
        ListNode left(0), right(0);
        ListNode *l = &left, *r = &right;
        while(head)
        {
            head->val < x ? 
                (l = l->next = head) : 
                (r = r->next = head);
            head = head->next;
        }
        r->next = NULL;
        l->next = right.next;
        return left.next;
    }
};
```