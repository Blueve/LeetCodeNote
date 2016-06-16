Word Ladder II
==========

## C++

Two-End BFS
```cpp
struct Node {
    string word;
    Node* parent;
    Node(string w, Node* p)
        :word(w), parent(p) {}
};

class Solution {
    vector<string> getPath(Node* node) {
        vector<string> path;
        while (node)
        {
            path.push_back(node->word);
            node = node->parent;
        }
        return path;
    }

    Node* newNode(string& word, Node* parent, unordered_map<string, unordered_map<Node*, Node*>> nodes) {
        auto& m = nodes[word];
        auto iter = m.find(parent);
        if (iter != m.end())
        {
            return iter->second;
        }
        else
        {
            Node* n = new Node(word, parent);
            m.insert({ parent, n });
            return n;
        }
    }

    vector<string> merge(Node* n1, Node* n2) {
        auto p1 = getPath(n1);
        auto p2 = getPath(n2);
        reverse(p1.begin(), p1.end());
        for (auto& s : p2) p1.push_back(s);
        return p1;
    }

public:
    vector<vector<string>> findLadders(string beginWord, string endWord, unordered_set<string> &wordList) {
        vector<vector<string>> result;
        unordered_map<string, unordered_map<Node*, Node*>> nodes;

        Node *begin = newNode(beginWord, NULL, nodes), *end = newNode(endWord, NULL, nodes);
        unordered_map<string, unordered_set<Node*>> bfs1 = { {beginWord, {begin}} };
        unordered_map<string, unordered_set<Node*>> bfs2 = { {endWord, {end}} };

        bool isLast = false, isReverse = false;
        while (bfs1.size())
        {
            unordered_map<string, unordered_set<Node*>> next;
            
            // Remove form unvisit list
            for (auto& node : bfs1)
                wordList.erase(node.first);
            
            // Expend bfs1
            for (auto& set : bfs1)
            for (auto node : set.second)
            {
                Node* n1 = node;
                string word = n1->word;
                for (int i(0); i < word.length(); ++i)
                {
                    char ch = word[i];
                    for (int j(0); j < 26; ++j)
                    {
                        word[i] = 'a' + j;
                        if (!wordList.count(word))
                            continue;
                        
                        auto iter = bfs2.find(word);
                        if(iter != bfs2.end())
                        {
                            // bfs1 meet bfs2
                            isLast = true;
                            for (auto n2 : bfs2[word])
                                result.push_back(isReverse ? merge(n2, n1) : merge(n1, n2));
                        }
                        else
                            next[word].insert( newNode(word, n1, nodes) );
                    }
                    word[i] = ch;
                }
            }

            if (isLast) break;
            
            // Make sure expend less set
            if (next.size() <= bfs2.size())
                swap(bfs1, next);
            else
            {
                swap(bfs1, bfs2);
                swap(bfs2, next);
                isReverse = !isReverse;
            }
        }
        return result;
    }
};
```
