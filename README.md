# Documentation
This repository contains technical documentation for Particracy Legacy and its web services. Particracy Legacy is an RP-based political simulation game. Free to play, works on the browser.

Keep up with the latest news and updates at https://prtcy.substack.com/.

## API

### Endpoints

1. `GET date/` - game year, month and remaining tickers for current month
2. `GET community/` - list of registered players
3. `GET newsfeed/` & `GET digest/` - aggregation of headlines from https://forum.prtcy.com
4. `GET stamps/` - activity data for registered players

### Notifications
The following messages are posted on Discord's private `#logs` and `#docket` channels. Additional messages exist only for the staging (and local/dev) environment as part of quality assurance.

If the API:

1. Fails to fetch the local storage of the date
2. Fails to fetch library data from the site (i.e. controllers) - reverts to local storage
3. Fails to retrieve local storage on case (2)
4. Skips a scrapper that is disabled from the site
5. Fails to scrape a source (i.e. list of users on the forums)
6. Fails to scrape the last page of a topic with new replies in the news section of the forums
7. Skips a post in the news section of the forums, due to insufficient content
8. Scrapes a national news post made by a user who's not primary or secondary in that nation
9. Fails to fetch AI-powered context
10. Detects a controller not having posted in the news section of the forums for >= 30 days
11. Detects the same case as (1) but for >= 60days

## UI

### Nation Portals
![Nation Portals @prtcy](imgs/nation-portals.png)

3 templates, all templates have the same fields.
 
#### Styling & layout

#### Basic details

#### Extra details (approval needed, auto-docket request)

#### Treaties and unions

#### State figures

#### Political parties

#### Quicklinks

#### Limits

1. Only primary can edit
2. Can edit once per game year
3. Cannot edit if inactive >= 7 days
4. Same rules for primary of author nation of union (if union full integration set to yes)
