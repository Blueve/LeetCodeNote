The Skyline Problem
==========

## C++


```cpp
class Solution {
public:
    vector<pair<int, int>> getSkyline(vector<vector<int>>& buildings) {
        multimap<int, int> points;
        for(auto& building : buildings)
        {
            points.emplace(building[0], building[2]);
            // Mark as end of building
            points.emplace(building[1], -building[2]);
        }
        
        multiset<int> heights;
        vector<pair<int, int>> corners;
        int x = -1, y = 0;
        for(auto& point : points)
        {
            if((x >= 0 && point.first != x) && 
               (corners.empty() || corners.rbegin()->second != y))
            {
                corners.emplace_back(x, y);
            }
            
            if(point.second >= 0)
            {
                // New height appear
                heights.insert(point.second);
            }
            else
            {
                // The building was scaned, remove it height
                heights.erase(heights.find(-point.second));
            }
            
            x = point.first;
            y = heights.rbegin() == heights.rend() ? 0 : *heights.rbegin(); // Current highest height
        }
        
        if(!corners.empty())
            corners.emplace_back(x, 0);
        
        return corners;
    }
};
```
