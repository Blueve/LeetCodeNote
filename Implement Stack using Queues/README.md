Implement Stack using Queues
==========

## C++

Two queue
```cpp
class Stack {
    queue<int> a, b;
public:
    // Push element x onto stack.
    void push(int x) {
        b.push(x);
        while(!a.empty())
        {
            b.push(a.front());
            a.pop();
        }
        a.swap(b);
    }

    // Removes the element on top of the stack.
    void pop() {
        a.pop();
    }

    // Get the top element.
    int top() {
        return a.front();
    }

    // Return whether the stack is empty.
    bool empty() {
        return a.empty();
    }
};
```
One queue
```cpp
class Stack {
    queue<int> q;
public:
    // Push element x onto stack.
    void push(int x) {
        q.push(x);
        int N(q.size());
        for(int i(1); i < N; ++i)
        {
            q.push(q.front());
            q.pop();
        }
    }

    // Removes the element on top of the stack.
    void pop() {
        q.pop();
    }

    // Get the top element.
    int top() {
        return q.front();
    }

    // Return whether the stack is empty.
    bool empty() {
        return q.empty();
    }
};
```
