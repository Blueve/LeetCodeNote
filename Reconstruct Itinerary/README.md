Reconstruct Itinerary
==========

## C++


```cpp
class Solution {
public:
    vector<string> findItinerary(vector<pair<string, string>> tickets) {
        map<string, multimap<string, bool>> graph;
        for(auto ticket : tickets)
            graph[ticket.first].insert({ticket.second, false});
        
        vector<string> result;
        dfs(graph, "JFK", tickets.size(), result);
        return result;
    }
    
    bool dfs(map<string, multimap<string, bool>>& graph, 
             string from, int n, vector<string>& result)
    {
        result.push_back(from);
        if(n == 0) return true;
        
        for(auto& to : graph[from])
        {
            if(!to.second)
            {
                to.second = true;
                if(dfs(graph, to.first, n - 1, result))
                    return true;
                to.second = false;
            }
        }
        result.pop_back();
        return false;
    }
};
```

Whitout backtracing. Topology sort.
```cpp
class Solution {
public:
    vector<string> findItinerary(vector<pair<string, string>> tickets) {
        map<string, multiset<string>> graph;
        for(auto ticket : tickets)
            graph[ticket.first].insert(ticket.second);
        
        vector<string> result;
        stack<string> dfs;
        dfs.push("JFK");
        while(!dfs.empty())
        {
            auto from = dfs.top();
            if(graph[from].empty())
            {
                result.push_back(from);
                dfs.pop();
            }
            else
            {
                dfs.push(*(graph[from].begin()));
                graph[from].erase(graph[from].begin());
            }
        }
        reverse(result.begin(), result.end());
        return result;
    }
};
```
