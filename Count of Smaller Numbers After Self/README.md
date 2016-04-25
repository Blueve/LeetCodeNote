Count of Smaller Numbers After Self
==========

## C++


```cpp
class Solution {
    struct TreeNode {
        TreeNode *left, *right;
        int val, n, count;
        TreeNode(int v)
            : val(v), n(1), count(0),
              left(NULL), right(NULL)
        {}
        
        int insert(int v)
        {
            if(val == v)
            {
                ++n;
                return count;
            }
            // Insert in left, cur node is bigger than new one,
            // then ignore cur node
            else if(val > v)
            {
                ++count;
                if(!left)
                {
                    left = new TreeNode(v);
                    return 0;
                }
                else
                    return left->insert(v);
            }
            // Insert in right, cur node is smaller than new one,
            // increase counter that cur node's count and cur node's copys.
            else
            {
                if(!right)
                {
                    right = new TreeNode(v);
                    return count + n;
                }
                else
                    return count + n + right->insert(v);
            }
        }
    };
    
public:
    vector<int> countSmaller(vector<int>& nums) {
        int n = nums.size();
        vector<int> counts(n);
        if(n <= 1)
            return counts;
            
        TreeNode *root = new TreeNode(nums.back());
        for(int i = n - 2; i >= 0; --i)
            counts[i] = root->insert(nums[i]);
            
        return counts;
    }
};
```
