Copy List with Random Pointer
==========

## C++


```cpp
/**
 * Definition for singly-linked list with a random pointer.
 * struct RandomListNode {
 *     int label;
 *     RandomListNode *next, *random;
 *     RandomListNode(int x) : label(x), next(NULL), random(NULL) {}
 * };
 */
class Solution {
public:
    RandomListNode *copyRandomList(RandomListNode *head) {
        unordered_map<RandomListNode*, RandomListNode*> record;
        return copy(head, record);
    }
    
    RandomListNode* copy(
        RandomListNode *node, 
        unordered_map<RandomListNode*, RandomListNode*>& record)
    {
        if(!node) return NULL;
        if(record.count(node)) return record[node];
        
        auto result = new RandomListNode(node->label);
        record[node] = result;
        
        result->random = copy(node->random, record);
        result->next = copy(node->next, record);
        return result;
    }
};
```
