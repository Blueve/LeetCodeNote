Palindrome Linked List
==========

## C++

  - Answer
  O(N) Time, O(N) Space
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
      bool isPalindrome(ListNode* head) {
          vector<int> list;
          
          ListNode* node = head;
          while(node)
          {
              list.push_back(node->val);
              node = node->next;
          }
          
          int N(list.size()), mid(N >> 1);
          for(int i(0); i < mid; ++i)
          {
              if(list[i] != list[N - i - 1]) return false;
          }
          return true;
      }
  };
  ```
  O(N) Time, O(1) Space, break input structure.
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
      bool isPalindrome(ListNode* head) {
          if(!head) return true;
          // Find mid node
          ListNode *mid = head, *node = head->next, *pre, *next;
          while(node && node->next && node->next->next)
          {
              mid = mid->next;
              node = node->next->next;
          }
          // Reverse tail
          pre = NULL;
          node = mid->next;
          while(node)
          {
              next = node->next;
              node->next = pre;
              pre = node;
              node = next;
          }
          // Compare
          node = head;
          while(pre) // tail always not less than head
          {
              if(node->val != pre->val) return false;
              node = node->next;
              pre = pre->next;
          }
          return true;
      }
  };
  ```