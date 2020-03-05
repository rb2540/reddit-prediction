# REDDIT SUBMISSION SCRAPER
------------

This script scrapes Reddit submissions in real-time, from a list of specified subreddits, and gets updated
values for the fields of each submission at specified time intervals. The script creates two CSV files. The first file contains every unique submission created while the script was running, each on a separate row. The second file contains every submission in the first file, with separate rows for the updated values at each time interval (i.e, score, num_comments, etc.).


# REQUIREMENTS
------------

This script was written in Python 3.6 and utilizes PRAW, the Python Reddit API Wrapper. PRAW can be installed
from the command line with pip.

A consistent internet connection must be maintained at all times while running this script. Re-running will 
cause the script to start over and create two new csv files. It will not continue checking submissions from a 
previous run for which it did not collect the full 24-hours of data.

Accessing the Reddit API and using this script requires a Reddit account. After making a reddit account, you
must also create a Reddit application by going to the "apps" tab in Preferences. The application-type selected
should be "script". Once your app is created, the following values must be used for the script:

* client_id
* client_secret
* username
* password

These values are entered when creating a Reddit instance, as in the load_reddit() function in this script. 
A "user_agent" must also entered. This is a unique identifier that helps Reddit determine the source of network
requests. The PRAW's documentation suggest the following format for user agent:

* windows:myredditapp:v1.2.3 (by /u/RedditUser)


# CONFIGURATION
-------------
 
 * Configure the reddit instance using the above instructions

 * If different time intervals for checking submissions are required, adjust the times in the 'mins_list' 
   variable as needed

 * Selecting the subreddits to scrape can be specified as a command-line argument, or hard-coded. This is 
   set in main(). The script already uses hard-coded subreddits. Simply change the 'subred' string to contain
   subreddits you wish to scrape, with each subreddit separated by a '+'. The command-line method is included
   but commented out. To use this method, simply un-comment the line '#subred = sys.argv[1]' and remove the 
   following line. The subreddits will then be selected from the command-line when running the script.   
   For example:

   C:\>python3 Reddit_Submission_Scraper.py AskReddit+Pics+Gifs+Poliitics

