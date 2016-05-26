Max Points on a Line
==========

## C++


```cpp
/**
 * Definition for a point.
 * struct Point {
 *     int x;
 *     int y;
 *     Point() : x(0), y(0) {}
 *     Point(int a, int b) : x(a), y(b) {}
 * };
 */
struct Slope {
   int dx, dy;
   Slope(int x, int y) : dx(x), dy(y) {}
   
   bool operator==(const Slope& othr) const {
       return dx * othr.dy == dy * othr.dx;
   }
};

struct hash_func {
    size_t operator()(const Slope& slope) const {
        if(!slope.dx) return 0;
        if(!slope.dy) return INT_MAX;
        return (slope.dx ? slope.dy / slope.dx : INT_MAX);;
    }
};

class Solution {
public:
    int maxPoints(vector<Point>& points) {
        if(points.empty())
            return 0;
        int n = points.size();
        int dx, dy, count(0);
        
        for(int i(0); i < n; ++i)
        {
            unordered_map<Slope, int, hash_func> hash;
            int same = 1, c = 0;
            for(int j(i + 1); j < n; ++j)
            {
                dx = points[i].x - points[j].x;
                dy = points[i].y - points[j].y;
                if(!dx && !dy)
                    ++same;
                else
                    c = max(c, ++hash[Slope(dx, dy)]);
            }
            count = max(count, c + same);
        }
        return count;
    }
};
```
