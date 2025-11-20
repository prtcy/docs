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

### Homepage

### Moods (Navigation)

### Nation Portals
![Nation Portals @prtcy](imgs/nation-portals.png)

3 templates, all templates have the same fields.
 
#### Styling & layout
1. Main bg color (hex, i.e. #394735)
2. Accent bg color (hex)
3. Main text color
4. Accent text color
5. Alignments (dropdown, start/center/end)
6. Heading (max 240 chars) - optional, default = title of nation (i.e. City States of Amudim)
7. Image bg (URL) - optional

#### Basic details
1. Nation title
2. Flag (URL)
3. Motto (max 240 chars, takes links, i.e. YouTube video)
4. Summary (max 800 chars)
5. National sport (dropdown, fetches options from library, options can be added/edited/removed on library)
6. National animal (same)
7. Political system (same)
8. Name of legislative body (max 70 chars) - optional
9. Total seats of legislative body (number, max 999, accepts 0 if name of legislative is empty)
10. Name of judiciary (max 70 chars) - optional
11. Name of government (max 70 chars) - default = Government of [Nation Name]

#### Extra details (approval needed, auto-docket request)
1. Nation name (max 70 chars)
2. Continent (dropdown)
3. Population (number)

#### Treaties and unions
1. Ratify/withdraw treaties (max 15, treaties can be added/edited/removed on library)
2. Union (dropdown, unions can be added/edited/removed on library), i.e. empires, federations, alliances
3. Full integration with union (yes/no, if yes, primary of author nation of union can edit portal) - default = no/member

#### State figures
1. HoS is HoG (yes/no) - default = no
2. HoS from union (yes/no, if yes, HoS automatically from author nation of union) - default = no

Figures (max 15)

1. Figure official title (max 800 chars)
2. Figure name of official (max 70 chars)
3. Figure image (URL) - optional
4. Figure summary (max 240 chars) - optional

#### Political parties
(max 15, can be 0 if name of legislative body is empty)

1. Political party name (max 70 chars)
2. Summary (max 240 chars)
3. Color (hex)
4. Seats in legislative body (number, max same as total seats in legislative body)
5. Name of leader (max 70 chars) - optional
6. Image of leader (URL) - optional
7. Image of political party (URL) - optional

#### Quicklinks
(max 15)

1. Quicklink title (max 70 chars)
2. Quicklink summary (max 240 chars)
3. Quicklink link (URL, accepts only from forum, wiki and site)
4. Quicklink image (URL) - optional

#### Limits

1. Only primary can edit
2. Can edit once per game year
3. Cannot edit if inactive >= 7 days
4. Same rules for primary of author nation of union (if union full integration set to yes)

### Yaps

-

Post "Full" Edit
Template is under Post Edit Templates > editpost. The WYSIWYG editor works with JS, which loads up PHP/HTML/CSS through an iframe - no idea why. To edit the styling, it requires direct server access (or via the repo's CI/CD) to jscripts/sceditor/styles/jquery.sceditor.mybb.css
