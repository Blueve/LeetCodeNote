Swap Nodes in Pairs
==========

## C++

  - Answer

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
      ListNode* swapPairs(ListNode* head) {
          ListNode *h = new ListNode(0);
          h->next = head;
          ListNode *node(head), *pre(h);
          while(node && node->next)
          {
              // Link to node->next
              pre->next = node->next;
              // Insert node after node->next
              node->next = pre->next->next;
              pre->next->next = node;
              
              pre = node;
              node = node->next;
          }
          node = h->next;
          delete h;
          return node;
      }
  };
  ```