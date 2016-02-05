Merge Two Sorted Lists
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
      ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
          if(l1 == NULL) return l2;
          if(l2 == NULL) return l1;
          
          ListNode *head = new ListNode(0);
          ListNode *p1 = l1, *p2 = l2, *p = head;
          while(p1 || p2)
          {
              if(p1 != NULL && (p2 == NULL || p1->val < p2->val))
              {
                  p->next = p1;
                  p1 = p1->next;
              }
              else
              {
                  p->next = p2;
                  p2 = p2->next;
              }
              p = p->next;
          }
          return head->next;
      }
  };
  ```