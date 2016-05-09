Word Ladder
==========

## C++

BFS
```cpp
class Solution {
public:
    int ladderLength(string beginWord, string endWord, unordered_set<string>& wordList) {
        wordList.erase(beginWord);
        int length = 1;
        // BFS
        queue<string> bfs;
        bfs.push(beginWord);
        while(!bfs.empty())
        {
            auto n = bfs.size();
            while(n--)
            {
                auto front = bfs.front();
                bfs.pop();
                
                if(front == endWord)
                    return length;
                
                for(int i(0); i < front.length(); ++i)
                {
                    char ch = front[i];
                    for(int j(0); j < 26; ++j)
                    {
                        front[i] = 'a' + j;
                        if(wordList.count(front))
                        {
                            bfs.push(front);
                            wordList.erase(front);
                        }
                    }
                    front[i] = ch;
                }
            }
            length++;
        }
        return 0;
    }
};
```
Better, Two-End BFS
```cpp
class Solution {
public:
    int ladderLength(string beginWord, string endWord, unordered_set<string>& wordList) {
        int length = 1;
        unordered_set<string> bfs1 = {beginWord};
        unordered_set<string> bfs2 = {endWord};
        
        while(bfs1.size())
        {
            ++length;
            unordered_set<string> next;
            
            // Expend bfs1
            for(auto& word : bfs1)
                wordList.erase(word);
            for(auto word : bfs1)
            {
                for(int i(0); i < word.length(); ++i)
                {
                    char ch = word[i];
                    for(int j(0); j < 26; ++j)
                    {
                        word[i] = 'a' + j;
                        if(!wordList.count(word))
                            continue;
                        // bfs1 Meet bfs2
                        if(bfs2.count(word))
                            return length;
                        next.insert(word);
                    }
                    word[i] = ch;
                }
            }
            // Expend small side in next time
            if(next.size() < bfs2.size())
                swap(bfs1, next);
            else
            {
                swap(bfs1, bfs2);
                swap(bfs2, next);
            }
        }
        return 0;
    }
};
```
