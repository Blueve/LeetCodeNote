Perfect Squares
==========

## C++

BFS
```cpp
class Solution {
public:
    int numSquares(int n) {
        if(n < 1) return 0;
        
        vector<int> square;
        for(int i(1); i * i <= n; ++i)
            square.push_back(i * i);
        
        queue<int> bfs;
        int cur, next, depth(1), slen(square.size() - 1);
        bfs.push(n);
        while(!bfs.empty())
        {
            int len = bfs.size();
            while(len --> 0)
            {
                cur = bfs.front();
                bfs.pop();
                
                for(int i = slen; i >= 0; --i)
                {
                    next = cur - square[i];
                    if(next > 0)
                        bfs.push(next);
                    else if (next == 0)
                        return depth;
                }
            }
            depth++;
        }
        
        return 0;
    }
};
```
Static DP, faster when this method is invoked frequently.
```cpp
class Solution {
public:
    int numSquares(int n) {
        static vector<int> DP {0};
        while (DP.size() <= n) {
            int m = DP.size(), squares = INT_MAX;
            for (int i(1); i * i <= m; ++i)
                squares = min(squares, DP[m - i * i] + 1);
            DP.push_back(squares);
        }
        return DP[n];
    }
};
```