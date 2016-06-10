Design Twitter
==========

## C++

getNewsFeed() - O(10) - O(1), 
postTweet() - O(F log(10) + log(10)) - O(F)
follow() - O(10 log(10) + log(F) + log(E)) - O(log(F) + log(E))
unfollow() - O(E 10 log(10) + log(F) + log(E)) - O(E)
```cpp
class Twitter {
    
    // userId, (tweets, followers, followees)
    unordered_map<int, tuple<set<int>, unordered_set<int>, unordered_set<int>>> users;
    unordered_map<int, set<int>> timeline;
    // id, tweetId
    int id = 0;
    unordered_map<int, int> tweetMap;
    
    // Add
    void Add(set<int>& tweets, int tweetId) {
        tweets.insert(id);
        tweetMap.insert({id, tweetId});
        if(tweets.size() > 10)
        {
            tweets.erase(tweets.begin());
        }
    }
    
    void PushToTimeline(set<int>& tl, set<int>& tweets) {
        for(auto tweet : tweets)
        {
            tl.insert(tweet);
            if(tl.size() > 10)
                tl.erase(tl.begin());
        }
    }
    
public:
    /** Initialize your data structure here. */
    Twitter() {
        
    }
    
    /** Compose a new tweet. */
    void postTweet(int userId, int tweetId) {
        auto& user = users[userId];
        auto& tweets = get<0>(user);
        auto& followers = get<1>(user);
        
        followers.insert(userId);
        get<2>(user).insert(userId);
        
        // Post to this user
        Add(tweets, tweetId);
        
        // Post to this user's followers' timeline
        for(auto followerId : followers)
        {
            Add(timeline[followerId], tweetId);
        }
        
        ++id;
    }
    
    /** Retrieve the 10 most recent tweet ids in the user's news feed. Each item in the news feed must be posted by users who the user followed or by the user herself. Tweets must be ordered from most recent to least recent. */
    vector<int> getNewsFeed(int userId) {
        vector<int> news;
        auto& tweets = timeline[userId];
        for(auto it = tweets.rbegin(); it != tweets.rend(); ++it)
        {
            news.push_back(tweetMap[*it]);
        }
        return news;
    }
    
    /** Follower follows a followee. If the operation is invalid, it should be a no-op. */
    void follow(int followerId, int followeeId) {
        if(followerId == followeeId) return;
        
        auto& followee = users[followeeId];
        auto& tl = timeline[followerId];
        
        // Put follwee's tweets to follower's timeline
        auto& tweets = get<0>(followee);
        PushToTimeline(tl, tweets);
        
        // Build relationship
        get<2>(users[followerId]).insert(followeeId);
        get<1>(followee).insert(followerId);
        
    }
    
    /** Follower unfollows a followee. If the operation is invalid, it should be a no-op. */
    void unfollow(int followerId, int followeeId) {
        if(followerId == followeeId) return;
        
        auto& tl = timeline[followerId];
        auto& user = users[followerId];
        auto& followees = get<2>(user);
        
        auto& followee = users[followeeId];
        // Discharge relationship
        get<2>(user).erase(followeeId);
        get<1>(followee).erase(followerId);
        
        // Rebuild timeline
        tl.clear();
        for(auto followee : followees)
        {
            PushToTimeline(tl, get<0>(users[followee]));
        }
    }
};

/**
 * Your Twitter object will be instantiated and called as such:
 * Twitter obj = new Twitter();
 * obj.postTweet(userId,tweetId);
 * vector<int> param_2 = obj.getNewsFeed(userId);
 * obj.follow(followerId,followeeId);
 * obj.unfollow(followerId,followeeId);
 */
```
