ST558Project1
================
Yuyao Liu
9/16/2020

# Required packages:

Please notice that the packages `httr`, `jsonlite` and `tidyverse` are
required to run the code to create your vignette.

``` r
library(httr)
library(jsonlite)
library(tidyverse)
```

# Query the data

## NHL records API

### List of franchise ID/name

1: “Montréal Canadiens”

2: “Montreal Wanderers”

3: “St. Louis Eagles”

4: “Hamilton Tigers”

5: “Toronto Maple Leafs”

6: “Boston Bruins”

7: “Montreal Maroons”

8: “Brooklyn Americans”

9: “Philadelphia Quakers”

10: “New York Rangers”

11: “Chicago Blackhawks”

12: “Detroit Red Wings”

13: “Cleveland Barons”

14: “Los Angeles Kings”

15: “Dallas Stars”

16: “Philadelphia Flyers”

17: “Pittsburgh Penguins”

18: “St. Louis Blues”

19: “Buffalo Sabres”

20: “Vancouver Canucks”

21: “Calgary Flames”

22: “New York Islanders”

23: “New Jersey Devils”

24: “Washington Capitals”

25: “Edmonton Oilers”

26: “Carolina Hurricanes”

27: “Colorado Avalanche”

28: “Arizona Coyotes”

29: “San Jose Sharks”

30: “Ottawa Senators”

31: “Tampa Bay Lightning”

32: “Anaheim Ducks”

33: “Florida Panthers”

34: “Nashville Predators”

35: “Winnipeg Jets”

36: “Columbus Blue Jackets”

37: “Minnesota Wild”

38: “Vegas Golden Knights”

### For the NHL record API, we have functions to show the endpoints:

### “endpoint”: function

“franchise”: franchise()

“franchise-team-totals” :
franchise\_team\_totals()

### The following endpoints should modify the specific franchise ID or franchise name you want.

“franchise-season-records” : franchise\_season(franchiseID)

“franchise-goalie-records” : franchise\_goalie(franchiseID)

“franchise-skater-records” : franchise\_skater(franchiseID)

``` r
franchise <- function(...){
  full_url <- "https://records.nhl.com/site/api/franchise"
  franchise <- fromJSON(content(GET(full_url), type = "text"), flatten = TRUE)
  franchise$data
}

franchise_team_totals <- function(...){
  full_url <- "https://records.nhl.com/site/api/franchise-team-totals"
  franchise_team_totals <- fromJSON(content(GET(full_url), type = "text"), flatten = TRUE)
  franchise_team_totals$data
}

franchise_season <- function(franchiseID,...){
  if(is.character(franchiseID)){franchiseID <- switch(franchiseID,"Montréal Canadiens" = 1, "Montreal Wanderers" = 2, "St.   Louis Eagles" = 3, "Hamilton Tigers" = 4, "Toronto Maple Leafs" = 5, "Boston Bruins" = 6, "Montreal Maroons" = 7, "Brooklyn Americans" = 8, "Philadelphia Quakers" = 9, "New York Rangers" = 10, "Chicago Blackhawks" = 11, "Detroit Red Wings" = 12, "    Cleveland Barons" = 13, "Los Angeles Kings" = 14, "Dallas Stars" = 15, "Philadelphia Flyers" = 16, "Pittsburgh Penguins" = 17, "St. Louis Blues" = 18, "Buffalo Sabres" = 19, "Vancouver Canucks" = 20, "Calgary Flames" = 21, "New York Islanders" = 22, "New Jersey Devils" = 23, "Washington Capitals" = 24, "Edmonton Oilers" = 25, "Carolina Hurricanes" = 26, "Colorado Avalanche" = 27, "Arizona Coyotes" = 28, "San Jose Sharks" = 29, "Ottawa Senators" = 30, "Tampa Bay Lightning" = 31, "Anaheim Ducks" = 32, "Florida Panthers" = 33, "Nashville Predators" = 34, "Winnipeg Jets" = 35, "Columbus Blue Jackets" = 36, "Minnesota Wild" = 37, "Vegas Golden Knights" = 38)
  }
  base_url <- "https://records.nhl.com/site/api/franchise-season-records"
  full_url <- paste0(base_url,"?cayenneExp=franchiseId=",franchiseID)
  franchise_season <- fromJSON(content(GET(full_url), type = "text"), flatten = TRUE)
  franchise_season$data
}

franchise_goalie <- function(franchiseID,...){
  if(is.character(franchiseID)){franchiseID <-switch(franchiseID,"Montréal Canadiens" = 1, "Montreal Wanderers" = 2, "St.   Louis Eagles" = 3, "Hamilton Tigers" = 4, "Toronto Maple Leafs" = 5, "Boston Bruins" = 6, "Montreal Maroons" = 7, "Brooklyn Americans" = 8, "Philadelphia Quakers" = 9, "New York Rangers" = 10, "Chicago Blackhawks" = 11, "Detroit Red Wings" = 12, " Cleveland Barons" = 13, "Los Angeles Kings" = 14, "Dallas Stars" = 15, "Philadelphia Flyers" = 16, "Pittsburgh Penguins" = 17, "St. Louis Blues" = 18, "Buffalo Sabres" = 19, "Vancouver Canucks" = 20, "Calgary Flames" = 21, "New York Islanders" = 22, "New Jersey Devils" = 23, "Washington Capitals" = 24, "Edmonton Oilers" = 25, "Carolina Hurricanes" = 26, "Colorado Avalanche" = 27, "Arizona Coyotes" = 28, "San Jose Sharks" = 29, "Ottawa Senators" = 30, "Tampa Bay Lightning" = 31, "Anaheim Ducks" = 32, "Florida Panthers" = 33, "Nashville Predators" = 34, "Winnipeg Jets" = 35, "Columbus Blue Jackets" = 36, "Minnesota Wild" = 37, "Vegas Golden Knights" = 38)}
  base_url <- "https://records.nhl.com/site/api/franchise-goalie-records?cayenneExp=franchiseId="
  full_url <- paste0(base_url,franchiseID)
  franchise_goalie <- fromJSON(content(GET(full_url), type = "text"), flatten = TRUE)
  franchise_goalie$data
}

franchise_skater <- function(franchiseID,...){
  if(is.character(franchiseID)){franchiseID <- switch(franchiseID,"Montréal Canadiens" = 1, "Montreal Wanderers" = 2, "St.   Louis Eagles" = 3, "Hamilton Tigers" = 4, "Toronto Maple Leafs" = 5, "Boston Bruins" = 6, "Montreal Maroons" = 7, "Brooklyn Americans" = 8, "Philadelphia Quakers" = 9, "New York Rangers" = 10, "Chicago Blackhawks" = 11, "Detroit Red Wings" = 12, "    Cleveland Barons" = 13, "Los Angeles Kings" = 14, "Dallas Stars" = 15, "Philadelphia Flyers" = 16, "Pittsburgh Penguins" = 17, "St. Louis Blues" = 18, "Buffalo Sabres" = 19, "Vancouver Canucks" = 20, "Calgary Flames" = 21, "New York Islanders" = 22, "New Jersey Devils" = 23, "Washington Capitals" = 24, "Edmonton Oilers" = 25, "Carolina Hurricanes" = 26, "Colorado Avalanche" = 27, "Arizona Coyotes" = 28, "San Jose Sharks" = 29, "Ottawa Senators" = 30, "Tampa Bay Lightning" = 31, "Anaheim Ducks" = 32, "Florida Panthers" = 33, "Nashville Predators" = 34, "Winnipeg Jets" = 35, "Columbus Blue Jackets" = 36, "Minnesota Wild" = 37, "Vegas Golden Knights" = 38)}
  base_url <- "https://records.nhl.com/site/api/franchise-skater-records?cayenneExp=franchiseId="
  full_url <- paste0(base_url,franchiseID)
  franchise_skater <- fromJSON(content(GET(full_url), type = "text"), flatten = TRUE)
  franchise_skater$data
}
```

## NHL stats API

### Please input the endpoint and/or teamID and/or season and modify them in the function to get the data you want.

If you preper one of the team, please input the ID.

NHL\_stats(modifier,teamID= ,season=,…)

For the NHL stats API, we have endpoints shown below:

“?expand=team.roster”

“?expand=person.names”

“?expand=team.schedule.next”

“?expand=team.schedule.previous”

“?expand=team.stats”

“?expand=team.roster\&season=” (You may choose the season you want, such
as“20142015”)

“?teamId=” (You may choose the teamId you want as a string, such
as“4,5,29”)

“?stats=statsSingleSeasonPlayoffs”

``` r
NHL_stats <- function(modifier, season= NA, teamstringID = NA, teamID= NA,...){
  base_url <- "https://statsapi.web.nhl.com/api/v1/teams"
  if (modifier == "?expand=team.roster"){
    full_url <- paste0(base_url,modifier)
    data <- fromJSON(content(GET(full_url), type = "text"), flatten = TRUE)
    data <- data$teams
    roster <- data.frame(id = data[1,]$id,data$roster.roster[[1]])
    for (i in 2:nrow(data)){
      new <- data.frame(id = data[i,]$id,data$roster.roster[[1]])
      roster <- rbind(roster,new)}
      dat <- full_join(data[,-30],roster, by = "id")
      if (!is.na(teamID)){
        dat <- filter(dat, id == teamID)
      }
      return(dat)
  }
    else if (modifier == "?expand=person.names"){
     full_url <- paste0(base_url,modifier)
     dat <- fromJSON(content(GET(full_url), type = "text"), flatten = TRUE)
     dat <- dat$teams
      if (!is.na(teamID)){
        dat <- filter(dat, id == teamID)
      }
      return(dat)
    }
    else if (modifier == "?expand=team.schedule.next") {
     full_url <- paste0(base_url,modifier)
     data <- fromJSON(content(GET(full_url), type = "text"), flatten = TRUE)
     dat <- data$teams
      if (!is.na(teamID)){
        dat <- filter(dat, id == teamID)
      }
      return(dat)
    }
  else if (modifier == "?expand=team.schedule.previous"){
    full_url <- paste0(base_url,modifier)
     data <- fromJSON(content(GET(full_url), type = "text"), flatten = TRUE)
     data <- data$teams
     dates <- data.frame(id=data[1,]$id,data$previousGameSchedule.dates[[1]]$games[[1]])
      for (i in 2:nrow(data)){
      new <- data.frame(id =data[i,]$id,data$previousGameSchedule.dates[[i]]$games[[1]])
      dates <- full_join(dates,new)}
      dat <- full_join(data[,-34],dates, by = "id")
      if (!is.na(teamID)){
        dat <- filter(dat, id == teamID)
      }
      return(dat)
  }
    else if (modifier == "?expand=team.stats"){
    full_url <- paste0(base_url,modifier)
    data <- fromJSON(content(GET(full_url), type = "text"), flatten = TRUE)
    data <- data$teams
    a <- cbind(data[1,-8],data$teamStats[[1]])
    a <- rbind(a,a)
    stats <- cbind(a[,-30], data$teamStats[[1]]$splits[[1]])
    for (i in 2:nrow(data)) {
      a <- cbind(data[i,-8],data$teamStats[[i]])
      a <- rbind(a,a)
      new <- cbind(a[,-30], data$teamStats[[i]]$splits[[1]])
      stats <- rbind(stats, new)
    }
    dat <- stats
     if (!is.na(teamID)){
        dat <- filter(dat, id == teamID)
      }
    return(dat)
    }
    
  else if((modifier == "?expand=team.roster&season=") && (!is.na(season))){
    full_url <- paste0(base_url,modifier,season)
      dat <- fromJSON(content(GET(full_url), type = "text"), flatten = TRUE)
      dat <- dat$teams
    if (!is.na(teamID)){
        dat <- filter(dat, id == teamID)
      }
      return(dat)
  }
  else if((modifier == "?teamId=") && (!is.na(teamstringID))){
    full_url <- paste0(base_url,modifier,teamstringID)
    dat <- fromJSON(content(GET(full_url), type = "text"), flatten = TRUE)
    dat <- dat$teams
    if (!is.na(teamID)){
    dat <- filter(dat, id == teamID)
    }
    return(dat)
  }
  else if (modifier == "?stats=statsSingleSeasonPlayoffs"){
    full_url <- paste0(base_url,modifier)
     dat <- fromJSON(content(GET(full_url), type = "text"), flatten = TRUE)
     dat <- dat$teams
      if (!is.na(teamID)){
        dat <- filter(dat, id == teamID)
      }
      return(dat)
    }
  else{
      stop("Please input the correct modifier")
  }
}
```

## One\_stop\_shop function

Now, we combine these functions to only one. If you are curious about
records API, please let type = “R”, and if you are curious about stats
API, please let type = “S”.

The function one\_stop\_shop works as: one\_stop\_shop(type=,
endpoint=,modifier=,franchise=,season=,teamdstringID=,
teamID=,)

``` r
one_stop_shop <- function(type, endpoint=NA, modifier=NA, franchiseID=NA, season = NA, teamstringID = NA, teamID=NA,...){
  if (type == "R") {
    if (endpoint == "franchise") {
      franchise()}
    else if (endpoint == "franchise-team-totals"){
      franchise_team_totals()
    }
    else if (endpoint == "franchise-season-records") {
      franchise_season(franchiseID)
    }
    else if (endpoint =="franchise-goalie-records") {
      franchise_goalie(franchiseID)}
    else if (endpoint == "franchise-skater-records"){
      franchise_skater(franchiseID)}
    else{stop("Incorrect API type or no match for type and endpoint")}
      }
    else if (type == "S"){
    NHL_stats(modifier,season,teamstringID, teamID)
  }
  else{
    stop("Incorrect API type or no match for type and endpoint")
  }
}
```

# Explore the data

## Join two returned datasets

``` r
join_a <- one_stop_shop("R", endpoint = "franchise-team-totals")
join_b <- one_stop_shop("S", modifier = "?expand=person.names")
join <-  left_join(join_a,join_b,by = "franchiseId")
head(join)
```

## Create two new variables

``` r
newData_1 <- one_stop_shop("R",endpoint = "franchise-goalie-records", franchiseID = 30)
newData_1 %>% mutate(winPercen = (1-losses/gamesPlayed)) %>% select(winPercen)

newData_2 <- one_stop_shop("R", endpoint = "franchise")
newData_2 %>% mutate(franchiseName = paste0(teamPlaceName," ",teamCommonName))

newData_3 <- one_stop_shop("R", endpoint = "franchise-team-totals")
for (i in 1:nrow(newData_3)) {
  if(is.na(newData_3$roadTies[i])){newData_3$roadTies[i] = 0}
}
road <- newData_3 %>% mutate(roadTotal=roadLosses+roadOvertimeLosses+roadTies+roadWins) 
head(road)
```

## Contingency Tables

``` r
data_4 <- one_stop_shop("S", modifier = "?expand=team.roster", teamID = 1)
table(data_4$position.code, data_4$position.type) %>% knitr::kable(caption = "position.code and position.type information")
```

|   | Defenseman | Forward | Goalie |
| - | ---------: | ------: | -----: |
| C |          0 |       5 |      0 |
| D |          5 |       0 |      0 |
| G |          0 |       0 |      2 |
| L |          0 |       4 |      0 |
| R |          0 |       1 |      0 |

position.code and position.type
information

``` r
data_5 <- one_stop_shop("S", modifier = "?expand=team.roster&season=", season = "20142015")
table(data_5$id, data_5$firstYearOfPlay) %>% knitr::kable(caption = "id and firstYearOfPlay information")
```

|    | 1917 | 1924 | 1926 | 1932 | 1967 | 1970 | 1972 | 1974 | 1979 | 1980 | 1982 | 1991 | 1992 | 1993 | 1995 | 1997 | 1998 | 2000 | 2011 | 2014 |
| -- | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| 1  |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    1 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |
| 2  |    0 |    0 |    0 |    0 |    0 |    0 |    1 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |
| 3  |    0 |    0 |    1 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |
| 4  |    0 |    0 |    0 |    0 |    1 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |
| 5  |    0 |    0 |    0 |    0 |    1 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |
| 6  |    0 |    1 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |
| 7  |    0 |    0 |    0 |    0 |    0 |    1 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |
| 8  |    1 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |
| 9  |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    1 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |
| 10 |    0 |    0 |    1 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |
| 12 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    1 |    0 |    0 |    0 |    0 |
| 13 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    1 |    0 |    0 |    0 |    0 |    0 |    0 |
| 14 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    1 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |
| 15 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    1 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |
| 16 |    0 |    0 |    1 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |
| 17 |    0 |    0 |    0 |    1 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |
| 18 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    1 |    0 |    0 |    0 |
| 19 |    0 |    0 |    0 |    0 |    1 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |
| 20 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    1 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |
| 21 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    1 |    0 |    0 |    0 |    0 |    0 |
| 22 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    1 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |
| 23 |    0 |    0 |    0 |    0 |    0 |    1 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |
| 24 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    1 |    0 |    0 |    0 |    0 |    0 |    0 |
| 25 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    1 |    0 |    0 |    0 |    0 |    0 |    0 |
| 26 |    0 |    0 |    0 |    0 |    1 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |
| 28 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    1 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |
| 29 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    1 |    0 |    0 |
| 30 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    1 |    0 |    0 |
| 52 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    1 |    0 |
| 53 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    1 |

id and firstYearOfPlay
information

``` r
data_6 <- one_stop_shop("S", modifier = "?expand=team.schedule.previous")
table(data_6$venue.timeZone.id, data_6$division.id) %>% knitr::kable(caption = "venue.timeZone.id and division.id information")
```

|                      | 15 | 16 | 17 | 18 |
| -------------------- | -: | -: | -: | -: |
| America/Chicago      |  0 |  5 |  0 |  0 |
| America/Denver       |  1 |  1 |  0 |  0 |
| America/Detroit      |  0 |  0 |  1 |  0 |
| America/Edmonton     |  1 |  0 |  0 |  0 |
| America/Los\_Angeles |  4 |  0 |  0 |  0 |
| America/Montreal     |  0 |  0 |  1 |  0 |
| America/New\_York    |  0 |  0 |  5 |  8 |
| America/Phoenix      |  1 |  0 |  0 |  0 |
| America/Toronto      |  0 |  0 |  1 |  0 |
| America/Vancouver    |  1 |  0 |  0 |  0 |
| America/Winnipeg     |  0 |  1 |  0 |  0 |

venue.timeZone.id and division.id
information

## Numerical Summaries

``` r
newData_1 %>% group_by(activePlayer) %>% summarise(avg = mean(gamesPlayed), med = median(gamesPlayed), var = var(gamesPlayed), IQR = IQR(gamesPlayed)) %>% knitr::kable()
```

| activePlayer |       avg |  med |       var |   IQR |
| :----------- | --------: | ---: | --------: | ----: |
| FALSE        |  61.90909 | 45.5 |  5336.372 | 65.75 |
| TRUE         | 119.00000 | 44.0 | 32082.500 | 63.00 |

``` r
newData_3 %>% group_by(gameTypeId) %>% summarise(avg = mean(gamesPlayed), med = median(gamesPlayed), var = var(gamesPlayed)) %>% knitr::kable()
```

| gameTypeId |       avg |  med |        var |
| ---------: | --------: | ---: | ---------: |
|          2 | 2028.5614 | 1511 | 4080134.43 |
|          3 |  190.4792 |  133 |   39910.55 |

``` r
newData_1 %>% group_by(activePlayer) %>% summarise(avg = mean(wins), med = median(wins), var = var(wins), quantile_25 = quantile(wins, probs = 0.25)) %>% knitr::kable()
```

| activePlayer |      avg |  med |      var | quantile\_25 |
| :----------- | -------: | ---: | -------: | -----------: |
| FALSE        | 24.18182 |  9.5 | 1316.537 |            1 |
| TRUE         | 53.20000 | 20.0 | 7020.700 |           11 |

## Plots

### (1) Bar Plot

The value first increased in around 1926 and reached its highest level
in around 1967. After that, the value waved and had peaks in 1979, 1990,
and 1997.

``` r
data_7 <- one_stop_shop(type = "S", modifier = "?expand=team.stats")
g1 <- ggplot(data = data_7, aes(x=firstYearOfPlay))
g1 + geom_bar() + labs(x = "First Year Of Play")
```

![](README_files/figure-gfm/unnamed-chunk-12-1.png)<!-- -->

### (2) Histogram

This histogram is right skewed, which means the losses number of most
team are below 50.

``` r
g2<-ggplot(newData_1,aes(x=losses, y =..density..))
g2+geom_histogram(bins = 20)+geom_density(adjust = 0.4,color="red",lwd=2,outline.type = "full")+labs(y="Density",title = "Histogram for Losses Number")
```

![](README_files/figure-gfm/unnamed-chunk-13-1.png)<!-- -->

### (3) Box Plot

The min, first quantile, median, third quantile, and max values of games
played with active players are all greater than that without active
players.

``` r
g3<- ggplot(newData_1,aes(x=activePlayer,y= gamesPlayed))
g3+geom_boxplot(size=0.3)+geom_point(position = "jitter",aes(group = activePlayer, col= activePlayer),size=1)+labs(title = "Boxplot for gamesPlayed")
```

![](README_files/figure-gfm/unnamed-chunk-14-1.png)<!-- -->

### (4) Scatter Plot

There seems to be a linear relationship between the number of shutouts
and wins. Theoratcally, the more wins a team has, the more shutouts it
possibaly creats.

``` r
g4<-ggplot(newData_3,aes(group=gameTypeId,x = shutouts, y = wins))
g4+geom_point(aes(color =gameTypeId),size=1)+geom_smooth(method = lm,color = "red")+labs(title = "Shutouts vs Wins") 
```

![](README_files/figure-gfm/unnamed-chunk-15-1.png)<!-- -->

### (5) Bar Plot

According to the ggplot, the number of falses on active players is about
three times the number of trues on active players.

``` r
g5 <- ggplot(data = newData_1, aes(x=activePlayer))
g5 + geom_bar() + labs(x = "Number of Active Players")
```

![](README_files/figure-gfm/unnamed-chunk-16-1.png)<!-- -->

### (6) Histogram

This histogram is right-skewed, which means the majority number of most
wins in one season are below 5. The record of most wins hits at around
40.

``` r
g6<-ggplot(newData_1,aes(x=mostWinsOneSeason, y =..density..))
g6+geom_histogram(bins = 20)+geom_density(adjust = 0.4,color="red",lwd=2,outline.type = "full")+labs(y="Density",title = "Histogram for Most Wins One Season")
```

![](README_files/figure-gfm/unnamed-chunk-17-1.png)<!-- -->
