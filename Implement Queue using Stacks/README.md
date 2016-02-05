Implement Queue using Stacks
==========

## C++

  - Answer

  ```cpp
  class Queue {
      stack<int> in;
      stack<int> out;
      
      void moveInToOut()
      {
          while(!in.empty())
          {
              out.push(in.top());
              in.pop();
          }
      }
      
  public:
      // Push element x to the back of queue.
      void push(int x) {
          in.push(x);
      }
  
      // Removes the element from in front of queue.
      void pop(void) {
          if(out.empty()) moveInToOut();
          out.pop();
      }
  
      // Get the front element.
      int peek(void) {
          if(out.empty()) moveInToOut();
          return out.top();
      }
  
      // Return whether the queue is empty.
      bool empty(void) {
          return in.empty() && out.empty();
      }
  };
  ```