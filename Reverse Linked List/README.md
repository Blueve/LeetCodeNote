Reverse Linked List
==========

## C++

N  A->B->
p  c  n
N<-A  B->
   p  c  n
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
    ListNode* reverseList(ListNode* head) {
        ListNode *pre = NULL, *cur = head, *next;
        while(cur)
        {
            next = cur->next;
            cur->next = pre;
            pre = cur;
            cur = next;
        }
        return pre;
    }
};
```
N->H->A->B
N->H->A<-B
         l
N->H<->A<-B
         l
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
    ListNode* reverseList(ListNode* head) {
        if(!head || !head->next) return head;
        ListNode *list = reverseList(head->next);
        head->next->next = head;
        head->next = NULL;
        return list;
    }
};
```