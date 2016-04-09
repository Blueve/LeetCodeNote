Merge k Sorted Lists
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
    ListNode* mergeKLists(vector<ListNode*>& lists) {
        auto cmp = [](ListNode* a, ListNode* b) { 
            return a->val > b->val;
        };
        priority_queue<ListNode*, vector<ListNode*>, decltype(cmp)> heap(cmp);
        
        for(auto& node : lists)
        {
            if(node) heap.push(node);
        }
        ListNode h(0), *cur = &h;
        while(!heap.empty())
        {
            auto node = heap.top();
            heap.pop();
            cur->next = node;
            cur = cur->next;
            if(node->next)
                heap.push(node->next);
        }
        return h.next;
    }
};
```
