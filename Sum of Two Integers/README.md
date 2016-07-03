Sum of Two Integers
==========

## C++


```cpp
class Solution {
public:
    int getSum(int a, int b) {
        int m = 0;
        unsigned int c = 0;
        for(int i = 0; i < 32; ++i)
        {
            c >>= 1;
            int l = a & 1;
            int r = b & 1;
            if(l & r & m)
            {
                c |= (1 << 31);
                m = 1;
            }
            else if(l & r || l & m || r & m)
            {
                m = 1;
            }
            else if(l || r || m)
            {
                c |= (1 << 31);
                m = 0;
            }
            else
            {
                m = 0;
            }
            
            a >>= 1;
            b >>= 1;
        }
        return c;
    }
};
```
