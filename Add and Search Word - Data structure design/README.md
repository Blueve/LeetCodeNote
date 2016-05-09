Add and Search Word - Data structure design
==========

## C++


```cpp
struct TireNode
{
    bool isEnd = false;
    TireNode* next[26] = {0};
};

class WordDictionary {
    TireNode *root = new TireNode();
    
    bool search(string& word, int pos, TireNode* root)
    {
        if(pos == word.length())
            return root->isEnd;
        
        if(word[pos] == '.')
        {
            for(int i(0); i < 26; ++i)
                if(root->next[i] && search(word, pos + 1, root->next[i]))
                    return true;
        }
        else
        {
            auto next = root->next[word[pos] - 'a'];
            if(next)
                return search(word, pos + 1, next);
        }
        return false;
    }
public:

    // Adds a word into the data structure.
    void addWord(string word) {
        auto node = root;
        for(auto ch : word)
        {
            ch -= 'a';
            if(!node->next[ch])
                node->next[ch] = new TireNode();
            node = node->next[ch];
        }
        node->isEnd = true;
    }

    // Returns if the word is in the data structure. A word could
    // contain the dot character '.' to represent any one letter.
    bool search(string word) {
        return search(word, 0, root);
    }
};

// Your WordDictionary object will be instantiated and called as such:
// WordDictionary wordDictionary;
// wordDictionary.addWord("word");
// wordDictionary.search("pattern");
```
