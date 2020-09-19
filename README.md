ST558Project1
================
Yuyao Liu
9/16/2020

# Required packages:

Please notice that the packages `httr`, `jsonlite` and `tidyverse` are
required to run the code to create your vignette.

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

“franchise-skater-records” :
franchise\_skater(franchiseID)

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

## One\_stop\_shop function

Now, we combine these functions to only one. If you are curious about
records API, please let type = “R”, and if you are curious about stats
API, please let type = “S”.

The function one\_stop\_shop works as: one\_stop\_shop(type=,
endpoint=,modifier=,franchise=,season=,teamdstringID=, teamID=,)

# Explore the data

## Join two returned datasets

## Create two new variables

## Contingency Tables

## Numerical Summaries

## Plots

### (1) Bar Plot

The value first increased in around 1926 and reached its highest level
in around 1967. After that, the value waved and had peaks in 1979, 1990,
and 1997.

### (2) Histogram

This histogram is right skewed, which means the losses number of most
team are below 50.

### (3) Box Plot

The min, first quantile, median, third quantile, and max values of games
played with active players are all greater than that without active
players.

### (4) Scatter Plot

There seems to be a linear relationship between the number of shutouts
and wins. Theoratcally, the more wins a team has, the more shutouts it
possibaly creats.

### (5) Bar Plot

According to the ggplot, the number of falses on active players is about
three times the number of trues on active players.

### (6) Histogram

This histogram is right-skewed, which means the majority number of most
wins in one season are below 5. The record of most wins hits at around
40.
