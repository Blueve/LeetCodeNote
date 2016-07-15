Guess Number Higher or Lower
==========

## C++


```cpp
// Forward declaration of guess API.
// @param num, your guess
// @return -1 if my number is lower, 1 if my number is higher, otherwise return 0
int guess(int num);

class Solution {
public:
    int guessNumber(int n) {
        int l = 1, r = n, m;
        while(true)
        {
            m = l + (r - l >> 1);
            switch(guess(m))
            {
                case -1:
                    r = m - 1;
                    break;
                case 1:
                    l = m + 1;
                    break;
                default:
                    return m;
            }
        }
    }
};
```
