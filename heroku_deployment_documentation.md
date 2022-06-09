# Deployment app to Heroku

In order to deploy the app to Heroku, you can follow the following simple steps.

1. Create a database on Heroku Postgres https://data.heroku.com/
2. Create 3 tables using the queries in sql_scripts folder.
3. Install Heroku CLI https://devcenter.heroku.com/articles/heroku-cli. Mac users can use `brew tap heroku/brew && brew install heroku`
4. Use Fixie https://devcenter.heroku.com/articles/fixie to get a static IP address (as Brawl stars API only allows static IP address)
5. Get Brawl stars API key from https://developer.brawlstars.com/ (using your static IP address provided by Fixie)
6. Add the key to your Heroku app's environment variable https://devcenter.heroku.com/articles/config-vars
    * `heroku config:set API_TOKEN=your_brawl_stars_api_key`
7. Deploy the app using Git https://devcenter.heroku.com/articles/git#:~:text=To%20deploy%20your%20app%20to,heroku%20main%20Initializing%20repository%2C%20done.
    * Add a remote to your local repository using e.g. `heroku git:remote -a example-app`
    * Deploy your code `git push heroku main`
8. Use Heroku Scheduler to schedule the jobs
    * `python scheduled_jobs/get_club_members.py` (running daily at 14:00 UTC)
    * `python scheduled_jobs/get_club_league_games.py` (running daily at 14:30 UTC)

Note: The club tag is hard-coded in **scheduled_jobs/get_club_members.py**. Remember to change it into your own club tag :) Voila!    
