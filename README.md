# REDDIT
## Collecting 5-years' worth of post information from the r/science subreddit and follow-up exploratory data analysis! 

The r/science subreddit is a forum where users can post about, and discuss, developments in any field of science. Users interact with such posts by 'upvoting' them, which is a way of expressing interest in the content of the submission.

The idea here was to collect information about all the posts from the r/science subreddit over the last 5 years (01/01/2015 to 04/21/2020, to be precise), and try to identify the common characteristics of posts that get a lot of visibility (i.e., posts with a high number of upvotes).
### Why is that important? 

To do so, I set out to collect the following information associated with posts on that subreddit: 
* Username of the poster
* Date and time of post
* Field of science relating to the submission (optional)
* Flair (optional). In this forum, flair is a way for the poster to display educational credentials, which is usually highest degree achieved, followed by field of said degree.
* Upvotes, i.e. our metric for positive reaction to the post, and a measure of how much visibility it achieved.


## Step 1: Data collection

### Talk about the data you're trying to collect (username, upvotes, date/time, "flair", field).

In order to collect the data, the [Reddit API](https://www.reddit.com/dev/api/) seemed like the obvious choice. Unfortunately, the official API does not enable users to collect post data within a specified date range, which is where the [Pushshift API](https://pushshift.io/api-parameters/) came in handy. Pushshift is a big data project that copies and stores Reddit submissions as they are posted on the website, and its API enables users to retrieve data from a specific date range. 

Using it, I was rapidly able to retrieve data for the ~ 250,000 posts that were made to the r/science subreddit in that 5-year span. A major caveat was that Reddit data, and specifically, the all-important upvotes, are dynamic –– meaning that the data retrieved from Pushshift was largely inaccurate. Luckily, to each Reddit submission is associated a static, unique identifier, which can be used to retrieve up-to-date, accurate information on these posts from the official Reddit API.

Unfortunately, the maximum number of calls that any given user can make to the Reddit API is set to 60 requests per minute, or 3600 requests per hour. A back-of-the-enveloppe calculation rapidly pointed to the fact that getting the desired data on the 250k posts of interest would take close to 3 days. With limited time on my hands, I decided to create 10 separate Reddit user accounts, which would each process a chunk of ~25k posts of the parent dataframe in parallel –– thus reducing data collection to an overnight operation.


### PushShift API allows you to collect data from a particular date range, which the Reddit API doesn't allow you to. 
### Step 1: collect the unique ID of each submission in this date range from the PushShift API. 
### Step 2: use the ID for each of these submissions to retrieve interesting and up-to-date information from the official Reddit API.

## Step 2: Data cleaning
## Step 3: Exploratory data analysis
