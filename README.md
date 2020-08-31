# REDDIT
## Collecting 5-years' worth of post information from the r/science subreddit and follow-up exploratory data analysis! 

The r/science subreddit is a forum where users can post about, and discuss, developments in any field of science. Users interact with such posts by 'upvoting' them, which is a way of expressing interest in the content of the submission.

The idea here was to collect information about all the posts from the r/science subreddit over the last 5 years (01/01/2015 to 04/21/2020, to be precise), and try to identify the common characteristics of posts that get a lot of visibility (i.e., posts with a high number of upvotes).
### Why is that important? 

To do so, I set out to collect the following information associated with posts on that subreddit: 
* Username of the poster
* Date and time of post
* Field of science relating to the submission (optional)
* Flair (optional). Flair is a way for the poster to display educational credentials, which is usually highest degree achieved, followed by field of said degree. These credentials are verified by the moderators of the forum.
* Upvotes, i.e. our metric for positive reaction to the post, and a measure of how much visibility it achieved.

## Data collection

In order to collect the data, the [Reddit API](https://www.reddit.com/dev/api/) seemed like the obvious choice. Unfortunately, the official API does not enable users to collect post data within a specified date range, which is where the [Pushshift API](https://pushshift.io/api-parameters/) came in handy. Pushshift is a big data project that copies and stores Reddit submissions as they are posted on the website, and its API enables users to retrieve data from a specific date range. 

Using it, I was rapidly able to retrieve data for the ~ 250,000 posts that were made to the r/science subreddit in that 5-year span. A major caveat was that Reddit data, and specifically, the all-important upvotes, are dynamic –– meaning that the data retrieved from Pushshift was largely inaccurate. Luckily, to each Reddit submission is associated a static, unique identifier, which can be used to retrieve up-to-date, accurate information on these posts from the official Reddit API.

Unfortunately, the maximum number of calls that any given user can make to the Reddit API is set to 60 requests per minute, or 3600 requests per hour. A back-of-the-enveloppe calculation rapidly pointed to the fact that getting the desired data on the 250k posts of interest would take close to 3 days. With limited time on my hands, I decided to create 10 separate Reddit user accounts, which would each process a chunk of ~25k posts of the parent dataframe in parallel –– thus reducing data collection to an overnight operation.

## Exploratory data analysis

In no particular order, a few of the interesting insights from this data.

### Some fields are more interesting to the community than others.

A quick glance shows that of the 250k posts of interest, ~150k have a field specified, with ~800 distinct fields. To get a sense of which fields tend to receive more upvotes, it was first necessary to extract the number of posts per distinct field, and to divide the number of posts to
