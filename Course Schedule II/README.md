Course Schedule II
==========

## C++


```cpp
class Solution {
public:
    vector<int> findOrder(int numCourses, vector<pair<int, int>>& prerequisites) {
        vector<set<int>> graph(numCourses);
        vector<int> inD(numCourses, 0);
        vector<int> queue(numCourses);
        int front(0), end(0), cur;
        
        for(auto p : prerequisites)
        {
            if(!graph[p.second].count(p.first))
            {
                graph[p.second].insert(p.first);
                ++inD[p.first];
            }
        }
        
        for(int i(0); i < numCourses; ++i)
            if(!inD[i]) queue[end++] = i;
        
        while(cur = end - front)
        {
            while(cur--)
            {
                int n = queue[front++];
                for(auto to : graph[n])
                {
                    if(--inD[to] == 0)
                        queue[end++] = to;
                }
            }
        }
        if(front == numCourses)
            return queue;
        else
            return {};
    }
};
```
