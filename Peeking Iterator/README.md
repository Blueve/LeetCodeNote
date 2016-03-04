Peeking Iterator
==========

## C++


```cpp
// Below is the interface for Iterator, which is already defined for you.
// **DO NOT** modify the interface for Iterator.
class Iterator {
    struct Data;
  Data* data;
public:
  Iterator(const vector<int>& nums);
  Iterator(const Iterator& iter);
  virtual ~Iterator();
  // Returns the next element in the iteration.
  int next();
  // Returns true if the iteration has more elements.
  bool hasNext() const;
};


class PeekingIterator : public Iterator {
public:
  PeekingIterator(const vector<int>& nums) : Iterator(nums) {
      // Initialize any member here.
      // **DO NOT** save a copy of nums and manipulate it directly.
      // You should only use the Iterator interface methods.
  }

    // Returns the next element in the iteration without advancing the iterator.
  int peek() {
        return Iterator(*this).next();
  }

  // hasNext() and next() should behave the same as in the Iterator interface.
  // Override them if needed.
  int next() {
      return Iterator::next();
  }

  bool hasNext() const {
      return retIterator::hasNext();
  }
};
```

```cpp
// Below is the interface for Iterator, which is already defined for you.
// **DO NOT** modify the interface for Iterator.
class Iterator {
    struct Data;
  Data* data;
public:
  Iterator(const vector<int>& nums);
  Iterator(const Iterator& iter);
  virtual ~Iterator();
  // Returns the next element in the iteration.
  int next();
  // Returns true if the iteration has more elements.
  bool hasNext() const;
};


class PeekingIterator : public Iterator {
    int cur;
    bool n;
public:
  PeekingIterator(const vector<int>& nums) : Iterator(nums) {
      // Initialize any member here.
      // **DO NOT** save a copy of nums and manipulate it directly.
      // You should only use the Iterator interface methods.
      n = Iterator::hasNext();
      cur = Iterator::hasNext() ? Iterator::next() : 0;
  }

    // Returns the next element in the iteration without advancing the iterator.
  int peek() {
        return cur;
  }

  // hasNext() and next() should behave the same as in the Iterator interface.
  // Override them if needed.
  int next() {
      int tmp(cur);
      n = Iterator::hasNext();
      if(n) cur = Iterator::next();
      return tmp;
  }

  bool hasNext() const {
     return n;
  }
};
```
