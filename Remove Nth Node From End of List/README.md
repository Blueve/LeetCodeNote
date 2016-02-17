Remove Nth Node From End of List
==========

## C++

  - Answer
  Using extra head to avoid missing head
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
      ListNode* removeNthFromEnd(ListNode* head, int n) {
          ListNode *h = new ListNode(0);
          h->next = head;
          ListNode *p1 = head, *p2 = head, *p3 = h, *result;
          // p1 go first
          while(n --> 1) p1 = p1->next;
          // p1 p2 go
          while(p1->next) p1 = p1->next, p2 = p2->next, p3 = p3->next;
          
          p3->next = p2->next;
          result = h->next;
          delete p2;
          delete h;
          return result;
      }
  };
  ```
  Whitout extra head
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
      ListNode* removeNthFromEnd(ListNode* head, int n) {
          ListNode *p1 = head, *p2 = head, *p3 = NULL, *r = head;
          // p1 go first
          while(n --> 1) p1 = p1->next;
          // p1 p2 go
          while(p1->next)
          {
              p3 = p2;
              p1 = p1->next, p2 = p2->next;
          }
          if(p3) p3->next = p2->next;
          else r = head->next;
          delete p2;
          return r;
      }
  };
  ```