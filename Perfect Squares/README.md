Perfect Squares
==========

## C++

  - Answer
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