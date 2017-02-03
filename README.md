# Final project - Event detection in Switzerland with Twitter

### Team
- Trinh Christophe ([@christophetrinh](https://github.com/christophetrinh))
- Ukachi Chibueze ([@Chibuu](https://github.com/Chibuu))
- Viola Mario ([@marioviola](https://github.com/marioviola))


### See the visualization
>To see the visualization, you've to run a HTTP server using python. Start the HTTP Server on port 8000 using ```python python -m SimpleHTTPServer 8000 ```. Then go to your favourite browser and type http://127.0.0.1:8000. Then, go to the repository Event_detection.


### Abstract

>Twitter is a social network and real-time communication service. This platform became a means of sharing information with others, around [140 million](https://www.bloomberg.com/news/articles/2016-06-02/snapchat-passes-twitter-in-daily-usage) daily users interact on this comminucation service. The purpose of this project is to use geolocated tweets to identify specific event in Switzerland. The aim is to understand the concentration of emerging tweets on a specific location about an event. The target is to provide an interactive map visualization which gather all the detected event over a period of time. The final result is based on our paired group data who focus on the data handling part. Their pipeline will not be detailed here for more information please take a look at their [Github repository](https://github.com/dsar/mobility_pattern_detection).

### Data description

A tweet object is define as "status updates” or "post" of a specific user, it can be embedded, replied to, liked, unliked and deleted. Tweet object consist of several fields discribe as follow :

| Field   |      Type      |  Description |
|---------|:---------------|:-------------|
| *userId* | Bigint(20) | The integer representation of the unique identifier for this Tweet.  |
| *text* |    UTF-8   |   The actual UTF-8 text of the status update. |
| *createdAt* | Timestamp | The UTC datetime that the user account was created on Twitter.  |
| *coordinates* | Collection of Float | Represents the geographic location of this Tweet as reported by the user or client application. The inner coordinates array is formatted as [geoJSON](http://geojson.org) (longitude first, then latitude). |

We are going to use the already provided dataset to perform most of our investigation. We will capatilise on the information given by active twitter users who regularly provide geolocated tweets, which are found to be from more than two distant locations.

### Main part

#### Data Cleaning/handling
The first step was to retrieve all the data from the cluster which covers 6 years (2010 to 2016). We keep only the geolocated tweets. We use [Geojson](http://geojson.org) format to encode the data structure with several properties such as coordinates, time ... The goal of this part is to retrieve all usable data for our visualization and prepare it with a specific format in order to manage the structure with visualization tools.

#### Visualization tools
The map is created using [Leaflet](http://leafletjs.com). We uses [d3js](https://d3js.org) javaScript library to create a dynamic visualisation and generate a svg overlay.

#### Final data used
Our final visualization show the data handled by our [paired team](https://github.com/dsar/mobility_pattern_detection). Basically, the dataframe given has the following structure :

| Field   |      Type      |  Description |
|---------|:---------------|:-------------|
| *hashtag* | String | The hashtag that represent the detected event. |
| *dayOfTweet* | datetime |   The day of the Tweet. |
| *usersPerHashtag* | Int | The number of users that Tweet on a specific event.  |
| *spamEvent* | Boolean | A spam detection based on the number of users that Tweet on a specific event. The threshold is fixed at 2. If there are less users that posted the hashtag than the threshold, the Tweet is considered as a spam. |
| *std* | Float | The standard deviation of posting time, the smaller the standard deviation of the posting time of the tweets, the more likely a true event is detected. |
| *approxLocation* | Coordinates | Approximation of the GPS location.  |

The final concatened dataframe contain 18694 event detected. We choose to reduce the number of users per event by removing the event with less than 5 users per event in order to reduce the number of event considered as spam. We assume that each event which has more than 5 users who tweet about it, has a high probability to be a real event. The following histogram show the proportion of discarded data.

[![Screen Shot 2017-01-30 at 22.29.24.png](https://s29.postimg.org/yx6q8dah3/Screen_Shot_2017_01_30_at_22_29_24.png)](https://postimg.org/image/91mzp68n7/)

The final data used for the visualization has 6400 event, we approximately reduce the original given dataframe by 34% with our assumption. 

### Feasibility and Risks

Not enough data after removing users that do not post or frequently post geolocated tweets.

### Deliverables

The final visualization consist of a map which provides the detected event location and a time chart which give the number of users who tweets about the event over a period of time. In order to visualize the event location on the map, select a specific period on the chart on the bottom of the map. The selection is done by a click on the begining of the choosen period, then release the mouse button when the desired end period is reached. You have the possibility to slide the selected period across the time. Each event is marked with a bubble with a radius depending on the number of tweets. By clicking on the specific event, a marker appear and provides the hashtag and the standard deviation of the period of the choosen event. The color of the bubble encode is related to the standard deviation of the period.

### Timeplan

- Week 1 : Start of the project and background research  
- Week 2 : Raw data cleaning 
- Week 3 - 4 : Data handling (geojson) and intermediate result  
- Week 5 - 6 : Data visualisation of data from our paired group 
- Week 7 : Presentation  