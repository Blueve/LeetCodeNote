Serialize and Deserialize Binary Tree
==========

## C++


```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Codec {
public:

    // Encodes a tree to a single string.
    string serialize(TreeNode* root) {
        if(!root) return "[]";
        string result = "[";
        
        queue<TreeNode*> q;
        q.push(root);
        while(!q.empty())
        {
            int n = q.size();
            while(n--)
            {
                auto node = q.front();
                q.pop();
                result += node ? to_string(node->val) + ',' : "null,";
                if(!node) continue;
                q.push(node->left);
                q.push(node->right);
            }
        }
        result.pop_back();
        return result + ']';
    }

    // Decodes your encoded data to tree.
    TreeNode* deserialize(string data) {
        int len = data.length() - 1;
        int num = 0, sign = 1;
        bool nil = false;
        TreeNode* root = NULL;
        queue<TreeNode**> q;
        q.push(&root);
        for(int i(1); i < len; ++i)
        {
            auto ch = data[i];
            if(ch == ',')
            {
                auto node = q.front();
                q.pop();
                if(!nil)
                {
                    *node = new TreeNode(sign * num);
                    q.push(&((*node)->left));
                    q.push(&((*node)->right));
                }
                sign = 1;
                num = nil = 0;
            }
            else if(ch == 'n')
            {
                nil = true;
                i += 3;
            }
            else if(ch == '-')
                sign = -1;
            else
            {
                num *= 10;
                num += ch - '0';
            }
        }
        return root;
    }
};

// Your Codec object will be instantiated and called as such:
// Codec codec;
// codec.deserialize(codec.serialize(root));
```
