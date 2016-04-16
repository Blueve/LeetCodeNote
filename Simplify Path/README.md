Simplify Path
==========

## C++


```cpp
class Solution {
public:
    string simplifyPath(string path) {
        string result, folder;
        vector<string> p;
        
        int len = path.length();
        for(int i(0); i < len; ++i)
        {
            if(path[i] == '/')
            {
                if(folder.empty() || folder == ".");
                else if(folder == "..")
                {
                    if(!p.empty()) p.pop_back();
                }
                else if(folder != ".")
                    p.push_back(folder);
                folder.clear();
            }
            else
                folder += path[i];
        }
        if(folder == "..")
        {
            if(!p.empty()) p.pop_back();
        }
        else if(!folder.empty() && folder != ".")
            p.push_back(folder);
            
        for(auto& f : p)
            result += '/' + f;
        return result.empty() ? "/" : result;
    }
};
```

Using stringstream instead of manual
```cpp
class Solution {
public:
    string simplifyPath(string path) {
        string result, folder;
        vector<string> p;
        stringstream input(path);
        while(getline(input, folder, '/'))
        {
            if(folder.empty() || folder == ".");
            else if(folder == "..")
            {
                if(!p.empty()) p.pop_back();
            }
            else if(folder != ".")
                p.push_back(folder);
        }
            
        for(auto& f : p)
            result += '/' + f;
        return result.empty() ? "/" : result;
    }
};
```
