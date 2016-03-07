Insertion Sort List
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
    ListNode* insertionSortList(ListNode* head) {
        ListNode h(0);
        ListNode *sorted, *next;
        while(head)
        {
            sorted = &h;
            // Find insert point
            while(sorted->next && sorted->next->val < head->val)
                sorted = sorted->next;
            // Insert after 'sorted'
            next = head->next;
            head->next = sorted->next;
            sorted->next = head;
            head = next;
        }
        return h.next;
    }
};
```
Faster, that solution can avoid worst case (Insert to sorted list's tail)
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
    ListNode* insertionSortList(ListNode* head) {
        ListNode h(0);
        ListNode *sorted = &h, *next;
        while(head)
        {
            next = head->next;
            // Avoid worst case
            if(!sorted->next || sorted->next->val > head->val)
                sorted = &h;
            // Find insert point
            while(sorted->next && sorted->next->val < head->val)
                sorted = sorted->next;
            // Insert after 'sorted'
            
            head->next = sorted->next;
            sorted->next = head;
            head = next;
        }
        return h.next;
    }
};
```