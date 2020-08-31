# REDDIT
## Collecting post information from the r/science subreddit and follow-up exploratory data analysis! 

The idea here was to collect information about all the posts from the r/science subreddit over the last 5 years (01/01/2015 to 04/21/2020, to be precise), and try to identify the common characteristics of posts that get a lot of visibility (i.e., posts with a high number of upvotes).

# Talk about the data you're trying to collect (username, upvotes, date/time, "flair", field).

In order to collect the data, the [Reddit API](https://www.reddit.com/dev/api/) seemed like the obvious choice. Unfortunately, the official API does not enable users to collect post data within a specified date range, which is where the [Pushshift API](https://pushshift.io/api-parameters/) came in handy. Pushshift is a big data project that copies and stores Reddit submissions as they are posted on the website, and its API enables users to retrieve data from a specific date range. 

In doing so, I was rapidly able to retrieve data for the ~ 250,000 posts that were made to the r/science subreddit in that 5-year span. A major caveat was that Reddit data, and specifically, the all-important upvotes, are dynamic – meaning that the data retrieved from Pushshift was, at the time of retrieval, largely inaccurate. Luckily, to each Reddit submission is associated a unique, static identifier; this handle was thus used to retrieve up-to-date, accurate information on these posts from the official Reddit API. 


### PushShift API allows you to collect data from a particular date range, which the Reddit API doesn't allow you to. 
### Step 1: collect the unique ID of each submission in this date range from the PushShift API. 
### Step 2: use the ID for each of these submissions to retrieve interesting and up-to-date information from the official Reddit API.

The basic idea here was to collect some 
