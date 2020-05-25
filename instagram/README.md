# Instagram

## Interface

```
postTweet(user_id, tweet_data, tweet_location, user_location, timestamp, …) 
generateTimeline(user_id, current_time, user_location, …)
markTweetFavorite(user_id, tweet_id, timestamp, …)
```

## Data Model

```
User: UserID, Name, Email, DoB, CreationData, LastLogin, etc. 
Tweet: TweetID, Content, TweetLocation, NumberOfLikes, TimeStamp, etc. User
Followo: UserdID1, UserID2 
FavoriteTweets: UserID, TweetID, TimeStamp
```

