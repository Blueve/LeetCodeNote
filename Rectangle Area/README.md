Rectangle Area
==========

## C++


```cpp
class Solution {
public:
    int computeArea(int A, int B, int C, int D, int E, int F, int G, int H) {
        int w1 = C - A, w2 = G - E, h1 = D - B, h2 = H - F;
        long long d1 = (long long)max(D, H) - min(B, F), d2 = (long long)max(C, G)   - min(A, E);
        int a1 = w1 * h1, a2 = w2 * h2;
        // Not intersection
        if(d1 > h1 + h2 || d2 > w1 + w2)
        {
            return a1 + a2;
        }
        else
        {
            return a1 + a2 - (h1 + h2 - d1) * (w1 + w2 - d2);
        }
    }
};
```
Simpler
```cpp
class Solution {
public:
    int computeArea(int A, int B, int C, int D, int E, int F, int G, int H) {
        int tmin = min(D, H), bmax = max(B, F), lmax = max(A, E), rmin = min(C, G);
        int a = (C - A) * (D - B) + (G - E) * (H - F);
        // Not intersection
        if(tmin < bmax || rmin < lmax)
            return a;
        else
            return a - (tmin - bmax) * (rmin - lmax);
    }
};
```
