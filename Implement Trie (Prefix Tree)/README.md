Implement Trie (Prefix Tree)
==========

## C++


```cpp
class TrieNode {
public:
    map<char, TrieNode*> next;
    bool end;
    // Initialize your data structure here.
    TrieNode() {
        end = false;
    }
};

class Trie {
public:
    Trie() {
        root = new TrieNode();
    }

    // Inserts a word into the trie.
    void insert(string word) {
        auto node = root;
        map<char, TrieNode*>::iterator iter;
        for(auto c : word)
        {
            if((iter = node->next.find(c)) != node->next.end())
                node = iter->second;
            else
            {
                node->next[c] = new TrieNode();
                node = node->next[c];
            }
        }
        node->end = true;
    }

    // Returns if the word is in the trie.
    bool search(string word) {
        auto node = root;
        map<char, TrieNode*>::iterator iter;
        for(auto c : word)
        {
            if((iter = node->next.find(c)) != node->next.end())
                node = iter->second;
            else
                return false;
        }
        
        return node->end;
    }

    // Returns if there is any word in the trie
    // that starts with the given prefix.
    bool startsWith(string prefix) {
        auto node = root;
        map<char, TrieNode*>::iterator iter;
        for(auto c : prefix)
        {
            if((iter = node->next.find(c)) != node->next.end())
                node = iter->second;
            else
                return false;
        }
        return true;
    }

private:
    TrieNode* root;
};

// Your Trie object will be instantiated and called as such:
// Trie trie;
// trie.insert("somestring");
// trie.search("key");
```

Faster. Because inputs are consist of lowercase letters `a-z`, we can using array instead of map.
```cpp
class TrieNode {
public:
    TrieNode* next[26] = {0};
    bool end;

    TrieNode() {
        end = false;
    }
};

class Trie {
public:
    Trie() {
        root = new TrieNode();
    }

    void insert(string word) {
        auto node = root;
        for(auto c : word)
        {
            c -= 'a';
            if(node->next[c])
                node = node->next[c];
            else
            {
                node->next[c] = new TrieNode();
                node = node->next[c];
            }
        }
        node->end = true;
    }

    bool search(string word) {
        auto node = root;
        for(auto c : word)
        {
            c -= 'a';
            if(node->next[c])
                node = node->next[c];
            else
                return false;
        }
        return node->end;
    }

    bool startsWith(string prefix) {
        auto node = root;
        for(auto c : prefix)
        {
            c -= 'a';
            if(node->next[c])
                node = node->next[c];
            else
                return false;
        }
        return true;
    }

private:
    TrieNode* root;
};
```