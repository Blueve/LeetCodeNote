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

A*, but time cost is highest, I have not figure out that : (
```cpp
struct state
{
    string str;
    int h; // Different between str and endWord
    int g; // Current length
    int f; // f = h + g

    state(string& s, int h, int g)
        : str(s), h(h), g(g)
    {
        f = h + g;
    }
};

struct cmp
{
    bool operator() (const state& a, const state& b)
    {
        return a.f > b.f;
    }
};

class Solution {
public:
    int ladderLength(string beginWord, string endWord, unordered_set<string>& wordList) {
        // Compute all word's 'h'
        map<string, int> h;
        for(auto& word : wordList)
        {
            int diff = 0;
            for(int i(0); i < endWord.length(); ++i)
            {
                if(word[i] != endWord[i])
                    ++diff;
            }
            h[word] = diff;
        }

        // A*
        priority_queue<state, vector<state>, cmp> open;
        unordered_set<string> openset;

        open.push(state(beginWord, 0, 1));
        openset.insert(beginWord);
        while(!open.empty())
        {
            auto s = open.top();
            open.pop();
            openset.erase(s.str);
            wordList.erase(s.str);

            if(s.str == endWord)
                return s.g;

            // Try expend current state
            auto& word = s.str;
            for(int i(0); i < word.length(); ++i)
            {
                char ch = word[i];
                for(char j('a'); j <= 'z'; ++j)
                {
                    word[i] = j;
                    // Because we inc 'g' only one in every step,
                    // if the word is already in openset,
                    // then the word's 'g' must equal or bigger than 'g' in openlist
                    // and that means we needn't fix 'g' in openlist
                    if(!wordList.count(word) || openset.count(word))
                        continue;

                    open.push(state(word, h[word], s.g + 1));
                    openset.insert(word);
                }
                word[i] = ch;
            }
        }
        return 0;
    }
};
```
