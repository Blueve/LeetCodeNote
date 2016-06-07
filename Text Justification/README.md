Text Justification
==========

## C++


```cpp
class Solution {
public:
    vector<string> fullJustify(vector<string>& words, int maxWidth) {
        vector<string> text;
        int i = 0, n = words.size();
        while(i < n)
        {
            string line;
            int width(0), wordsLen(0), begin(i);
            while(i < n && width <= maxWidth)
            {
                string word = words[i++];
                wordsLen += word.length();
                width = wordsLen + (i - begin) - 1;
            }
            if(width > maxWidth)
                wordsLen -= words[--i].length();
            
            int count = i - begin - 1;
            int space = maxWidth - wordsLen;
            
            // Check if only one words
            if(count == 0)
            {
                text.push_back(words[begin] + string(space, ' '));
                continue;
            }
            // Check if last line
            if(i == n)
            {
                for(int k(begin); k < i; ++k)
                    line += words[k] + ' ';
                text.push_back(line + string(space - (i - begin), ' '));
                continue;
            }
            
            // Merge words in a line
            int interval = space / count;
            int extra = space % count;
            for(int k(0); k < count; ++k)
            {
                line += words[begin + k];
                line += string(k < extra ? interval + 1 : interval, ' ');
            }
            line += words[i - 1];
            text.push_back(line);
        }
        return text;
    }
};
```
