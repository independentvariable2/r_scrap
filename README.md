r_scrapper (reddit scrapper), is a python package that allows simple scrapping of reddit's subreddits and submissions.
It was created due to the fact that reddit's official PRAW “Python Reddit API Wrapper” doesn't let you get the list of subreddits/submissions easily.

Officially supported on python 3.6+. Recommended installation via pip.
    pip install r_scrapper

With it installed, lets import (example):
    from r_scrap import api as r_scrap_api

--------------------------------------------------------------------------------------
    
To get subbreddit_index, subbreddits:
    subreddit_index, subreddits = r_scrap_api.fetch_subreddits(limit=None, export=False, user_agent='subreddit.fetch.bot')
limit - <int/None> determines amount of subreddits fetched, None for all (default: None)
export - <True/False> export the data to files? (default: False)
user_agent - <str> user agent used to connect to reddit (default: 'subreddit.fetch.bot')

subreddit_index - list of dictionaries {id, name, title, url} for quick access
subreddits - list of dictionaries {...subreddit}

To get submission_index_ submissions:
    #Code from prev example
    for subreddit in subreddits:
		submission_index, submissions = r_scrap_api.fetch_submissions(subreddit, limit=None, export=False, user_agent='submission.fetch.bot')
subreddit - <dict> subreddit dictionary fetched in prev example
limit - <int/None> determines amount of submissions fetched, None for all (default: None)
export - <True/False> export the data to files? (default: False)
user_agent - <str> user agent used to connect to reddit (default: 'subreddit.fetch.bot')

submission_index - dictionary {subreddit_id, subreddit_title, submissions[{id, name, title, permalink]}
subreddits = list of dictionaries {...submission}

All the logs will get saved in ./r_scrap.log file