Top K Frequent Elements
==========

## C++


```cpp
class Solution {
public:
    vector<int> topKFrequent(vector<int>& nums, int k) {
        auto cmp = [](pair<int, int>& lhs, pair<int, int>& rhs) {
            return lhs.second > rhs.second;
        };
        priority_queue<pair<int, int>, vector<pair<int, int>>, decltype(cmp)> heap(cmp);
        unordered_map<int, int> hT;
        
        for(auto n : nums)
            ++hT[n];
        
        for(auto& item : hT)
        {
            if(k --> 0) heap.push(item);
            else if(heap.top().second < item.second)
            {
                heap.pop();
                heap.push(item);
            }
        }
        
        vector<int> result;
        while(!heap.empty())
        {
            result.push_back(heap.top().first);
            heap.pop();
        }
        return result;
    }
};
```
