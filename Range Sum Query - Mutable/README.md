Range Sum Query - Mutable
==========

## C++

Log(N) Query, Log(N) Update
```cpp
struct SegmentTreeNode {
    int sum;
    SegmentTreeNode *left, *right;
    SegmentTreeNode() {}
};

class NumArray {
    SegmentTreeNode* root;
    int n;
    
    SegmentTreeNode* build(vector<int>& nums, int l, int r)
    {
        if(l > r) return NULL;
        
        auto node = new SegmentTreeNode();
        if(l == r)
            node->sum = nums[l];
        else
        {
            int m = l + (r - l >> 1);
            node->left = build(nums, l, m);
            node->right = build(nums, m + 1, r);
            node->sum = node->left->sum + node->right->sum;
        }
        return node;
    }
    
    void update(SegmentTreeNode* root, int l, int r, int i, int val)
    {
        if(l == r)
            root->sum = val;
        else
        {
            int m = l + (r- l >> 1);
            if(i <= m)
                update(root->left, l, m, i, val);
            else
                update(root->right, m + 1, r, i, val);
            root->sum = root->left->sum + root->right->sum;
        }
    }
    
    int sumRange(SegmentTreeNode* root, int l, int r, int begin, int end)
    {
        if(l == begin && r == end)
            return root->sum;
        
        int m = l + (r - l >> 1);
        if(end <= m)
            return sumRange(root->left, l, m, begin, end);
        else if(m < begin)
            return sumRange(root->right, m + 1, r, begin, end);
        else
            return sumRange(root->left, l, m, begin, m) +
                   sumRange(root->right, m + 1, r, m + 1, end);
    }
    
public:
    NumArray(vector<int> &nums)
        : n(nums.size() - 1) {
        root = build(nums, 0, n);
    }

    void update(int i, int val) {
        update(root, 0, n, i, val);
    }

    int sumRange(int i, int j) {
        return sumRange(root, 0, n, i, j);
    }
};


// Your NumArray object will be instantiated and called as such:
// NumArray numArray(nums);
// numArray.sumRange(0, 1);
// numArray.update(1, 10);
// numArray.sumRange(1, 2);
```
