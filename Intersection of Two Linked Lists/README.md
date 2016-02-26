Intersection of Two Linked Lists
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
      ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
          if(!headA || !headB) return false;
          
          ListNode *pA = headA, *pB = headB;
          int a(0), b(0);
          // Go listA's tail
          while(pA->next) ++a, pA = pA->next;
          // Go listB's tail
          while(pB->next) ++b, pB = pB->next;
          
          if(pA != pB) return false; /// not intersection
          
          pA = headA, pB = headB;
          if(a < b) swap(pA, pB), swap(a, b);
          for(int i(a - b); i > 0; --i)
              pA = pA->next;
          
          while(pA != pB)
          {
              pA = pA->next;
              pB = pB->next;
          }
          return pA;
      }
  };
  ```
  Better
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
      ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
          if(!headA || !headB) return false;
          
          ListNode *pA = headA, *pB = headB;
          while(pA && pB)
          {
              if(pA == pB) return pA;
              pA = pA->next;
              pB = pB->next;
              
              if(pA == pB) return pA; // Both NULL will ret.
              if(!pA) pA = headB;
              if(!pB) pB = headA;
          }
      }
  };
  ```