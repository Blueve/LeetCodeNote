LRU Cache
==========

## C++

get: O(logN)
set: O(logN)
```cpp
class LRUCache{
    unordered_map<int, int> cache;
    unordered_map<int, int> key_index;
    map<int, int> index;
    
    int capacity;
    int count;
    
    // logN
    void updateIndex(int key)
    {
        index.erase(key_index[key]);
        key_index[key] = count;
        index[count++] = key;
    }
    
public:
    LRUCache(int capacity)
        : capacity(capacity), count(0)
    { }
    
    // O(logN)
    int get(int key) {
        auto item = cache.find(key);
        if(item == cache.end())
            return -1;
        updateIndex(key);
        return item->second;
    }
    
    // O(logN)
    void set(int key, int value) {
        // Check if this pair in cache
        auto item = cache.find(key);
        if(item != cache.end())
        {
            item->second = value;
            updateIndex(key);
        }
        else
        {
            if(cache.size() == capacity)
            {
                // Remove least recently used item
                auto item = index.begin();
                cache.erase(item->second);
                key_index.erase(item->second);
                index.erase(item->first);
            }
            cache[key] = value;
            key_index[key] = count;
            index[count++] = key;
        }
    }
};
```

get: O(1)
set: O(1)
```cpp
class LRUCache{
    // key -> (value, list_node)
    unordered_map<int, pair<int, list<int>::iterator>> cache;
    list<int> index;
    
    int capacity;
    
    void updateIndex(list<int>::iterator node)
    {
        // move node to index_list's begin
        index.splice(index.begin(), index, node);
    }
public:
    LRUCache(int capacity)
        : capacity(capacity)
    { }
    
    // O(1)
    int get(int key) {
        auto item = cache.find(key);
        if(item == cache.end())
            return -1;
        updateIndex(item->second.second);
        return item->second.first;
    }
    
    // O(1)
    void set(int key, int value) {
        // Check if this pair in cache
        auto item = cache.find(key);
        if(item != cache.end())
        {
            item->second.first = value;
            updateIndex(item->second.second);
        }
        else
        {
            if(cache.size() == capacity)
            {
                // Remove least recently used item
                cache.erase(index.back());
                index.pop_back();
            }
            index.push_front(key);
            cache[key] = make_pair(value, index.begin());
        }
    }
};
```