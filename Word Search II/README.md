Word Search II
==========

## C++

There is a risk of memory leak, 
```cpp
class Solution {
    struct TrieNode {
        string word;
        TrieNode* next[26] = {0};
    };
    
    TrieNode* root;
    
    void insert(string& word) {
        auto node = root;
        for(auto c : word)
        {
            auto ch = c - 'a';
            if(node->next[ch])
                node = node->next[ch];
            else
            {
                node->next[ch] = new TrieNode();
                node = node->next[ch];
            }
        }
        node->word = word;
    }
    
    void destory(TrieNode* node) {
        for(int i(0); i < 26; ++i)
            if(node->next[i])
                destory(node->next[i]);
        delete node;
    }
    
    void dfs(vector<vector<char>>& board, vector<string>& result, int i, int j, TrieNode* node) {
        if(i < 0 || j < 0 || i == board.size() || j == board[0].size() || 
           !board[i][j] || !node->next[board[i][j] - 'a'])
            return;
        
        auto c = board[i][j];
        node = node->next[c - 'a'];
        if(!node->word.empty())
            result.push_back(move(node->word));
        
        board[i][j] = 0;
        dfs(board, result, i + 1, j, node);
        dfs(board, result, i, j + 1, node);
        dfs(board, result, i - 1, j, node);
        dfs(board, result, i, j - 1, node);
        board[i][j] = c;
    }
    
public:
    vector<string> findWords(vector<vector<char>>& board, vector<string>& words) {
        root = new TrieNode();
        for(auto& word : words)
            insert(word);
        
        vector<string> result;
        int n = board.size(), m = board[0].size();
        for(int i(0); i < n; ++i)
            for(int j(0); j < m; ++j)
                dfs(board, result, i, j, root);
        // Uncomment the code below can avoid memory leak
        // destory(root);
        return result;
    }
};
```
