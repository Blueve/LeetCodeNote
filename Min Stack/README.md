Min Stack
==========

## C++

  - Answer

  ```cpp
  class MinStack {
      stack<int> data;
      stack<int> min;
  public:
      void push(int x) {
          data.push(x);
          if(min.empty() || x <= min.top())
              min.push(x);
      }
  
      void pop() {
          if(top() == min.top())
              min.pop();
          data.pop();
      }
  
      int top() {
          return data.top();
      }
  
      int getMin() {
          return min.top();
      }
  };
  ```