# Final project - Mobility patterns in Switzerland with Twitter

### Team
- Trinh Christophe ([@christophetrinh](https://github.com/christophetrinh))
- Ukachi Chibueze ([@Chibuu](https://github.com/Chibuu))
- Viola Mario ([@marioviola](https://github.com/marioviola))

### Abstract

>The aim of this project is to use geolocated tweets to identify the travelling patterns across the Swiss-border. We will consider the radius of gyration (ROG) to measure the distance convered by the users over a period of time. 
The reference point for each user will be chosen as the location at which the most frequent geo-located tweets were made. 
We will query individual tweets to decide the end points for the ROG. This will be categoried by the journeys made between cities and also on a temporal basis to demonstrate the dynamic changes over a period of time.  

### Data description

A tweet object is define as “status updates” or "post" of a specific user, it can be embedded, replied to, liked, unliked and deleted. Tweet object consist of several fields discribe as follow :

| Field   |      Type      |  Description |
|---------|:---------------|:-------------|
| *user* | [Users](https://dev.twitter.com/overview/api/users) | The user who posted this Tweet. |
| *text* |    String   |   The actual UTF-8 text of the status update. |
| *id* | Int64 | The integer representation of the unique identifier for this Tweet.  |
| *coordinates* | Coordinates | Represents the geographic location of this Tweet as reported by the user or client application. The inner coordinates array is formatted as [geoJSON](http://geojson.org) (longitude first, then latitude). |

We are going to use the already provided dataset to perform most of our investigation. We will capatilise on the information given by active twitter users who regularly provide geolocated tweets, which are found to be from more than two distant locations.

We will enhance the dataset by collecting (with Twitter API - [REST API](https://dev.twitter.com/rest/public)) more geo-located tweets if there are insufficent data to make a reasonable conclusion.


### Feasibility and Risks

Not enough data after removing users that do not post or frequently post geolocated tweets.

### Deliverables
- Define/quantifying metrics for active users infrequent tweeters, categorising data by distance and identifying key words from tweet searches and hashtags.

- Data cleaning by detecting humans from advertisements, web gaming and twitter robots, classifying users by cities, frequent geo-located tweets e.t.c.

- Provide different visualisation methodologies. Please see the graphics section for more information.

- Bonus: machine learning to predict the migration flow due to unexpected events.

### Graphics

We plan on using [D3.js](https://d3js.org) javaScript library to create a dynamic visualisation of mobility flows of the users.

### Timeplan

- Week 1 : Start of the project and background research  
- Week 2 : Data cleaning  
- Week 3 - 4 : Data handling and intermediate result  
- Week 5 - 6 : Data visualisation  
- Week 7 : Presentation  