H-Index
==========

## C++


```cpp
class Solution {
public:
    int hIndex(vector<int>& citations) {
        int N(citations.size());
        vector<int> hashTable(N + 1);
        // Build hash table
        for(auto c : citations)
            ++hashTable[c < N ? c : N];
        // Find max h-index
        for(int i(N), count(0); i >= 0; --i)
        {
            count += hashTable[i];
            if(count >= i) return i;
        }
    }
};
```
