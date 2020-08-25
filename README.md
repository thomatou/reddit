# REDDIT
## Collecting post information from the r/science subreddit and follow-up exploratory data analysis! 

The idea here was to collect information about all the posts from the r/science subreddit over the last 5 years (01/01/2015 to 04/21/2020, to be precise), and try to identify the common characteristics of posts that get a lot of visibility (i.e., posts with a high number of upvotes).

The first hurdle was... 

### PushShift API allows you to collect data from a particular date range, which the Reddit API doesn't allow you to. 
### Step 1: collect the unique ID of each submission in this date range from the PushShift API. 
### Step 2: use the ID for each of these submissions to retrieve interesting and up-to-date information from the official Reddit API.

The basic idea here was to collect some 
