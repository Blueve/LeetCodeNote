Reverse Linked List
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
      ListNode* reverseList(ListNode* head) {
          ListNode *pre, *node, *tmp;
          pre = NULL;
          node = head;
          while(node)
          {
              tmp = node->next;
              node->next = pre;
              pre = node;
              node = tmp;
          }
          return pre;
      }
  };
  ```