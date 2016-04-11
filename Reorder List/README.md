Reorder List
==========

## C++

O(N) Space
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
    void reorderList(ListNode* head) {
        if(!head) return;
        ListNode *cur;
        vector<ListNode*> list;
        cur = head;
        while(cur)
        {
            list.push_back(cur);
            cur = cur->next;
        }
        int n = list.size() - 1, i = 0;
        cur = head;
        while(i < n)
        {
            list[n]->next = cur->next;
            cur->next = list[n];
            cur = cur->next->next;
            i++, n--;
        }
        if(list.size() & 1) cur->next = NULL;
        else cur->next->next = NULL;
    }
};
```

O(1) Space
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
    void reorderList(ListNode* head) {
        if(!head) return;
        // Find mid node
        ListNode *slow, *fast;
        slow = fast = head;
        fast = fast->next;
        while(fast && fast->next)
        {
            fast = fast->next->next;
            slow = slow->next;
        }
        ListNode *mid = slow->next;
        slow->next = NULL;
        
        // Reverse right part
        if(!mid) return;
        ListNode *cur = mid, *next = mid->next;
        cur->next = NULL;
        while(next)
        {
            auto tmp = next->next;
            next->next = cur;
            cur = next;
            next = tmp;
        }
        mid = cur;
        
        // Merge two parts
        cur = head, next = mid;
        while(next)
        {
            auto tmp = next->next;
            next->next = cur->next;
            cur->next = next;
            cur = cur->next->next;
            next = tmp;
        }
    }
};
```
