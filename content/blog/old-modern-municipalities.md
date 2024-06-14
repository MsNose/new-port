---
title: "Mapping: Old elections results with modern municipalities"
date: 2024-01-26T12:49:27+06:00
featureImage: images/allpost/netherlands_elections.jpg
postImage: images/blog/dutch-elections/title1.jpg
tags: Tableau
categories: blog
---

I want to see on a map how people voted in 1956 in the Netherlands. But how can I dot that if the geographical units have changed since then? Tableau does not have historical map capabilities. So, the only solution is connecting the old municipalities to the current territories. Back then there were 1008 of them, and now just 342. Note that I excluded Flevoland, the artificially created province from the analysis.

### 1. Connect the data

I have one sheet with the election results of 1956, with municipality code, name, party name, and the corresponding number of votes. It may be more userfriendly in excel to have the different parties in different columns, but for Tableau this is the perfect format. This makes it much easier to compare the different parties, which are just categories under a variable. 

![](/images/blog/dutch-elections/1.png)


The other sheet contains the old municipality names and the new equivalents. Hence, teh two sheets can be merged by making a connection between the municipality names of the voting data set (RegioNaam) and the old municipality names of the equals sheet.

![](/images/blog/dutch-elections/2.png)


### 2. Table with number of votes 
Now pulling the Party Names to the column and the new municipality names, Tableau will automatically transform the data due to the connection we just made. Add the Number of Votes (which belong to the 1956 elections) to the text field.

![](/images/blog/dutch-elections/3.png)



### 3.  Percentages
This is all nice, but we are rather interested in the percentages, than the number of votes. Create a Table Calculculation for the number of votes, and choose the percentage of total from the row. This way we see the voting percentages for each municipality. 

![](/images/blog/dutch-elections/4.png)


### 4. Map
This is of course more impactful on a map. The goal is to see the catholic vote share percentage (KVP) for each map. Before this, make sure that the new municipalities are counted as geographical locations. Define them as counties and choose the Netherlands as location for the map.

![](/images/blog/dutch-elections/5.png)

Now that longitude and latitude measures are accurate, we can create the map. Important: Resist the urge of creating a new sheet and trying to strategically place pills on it. After all, we have all the information we want to see exactly on this table calculation. Just simply go to show me and change the view to map. Now you have maps for each party. Hide all of them except for the catholic, and there is your map!

![](/images/blog/dutch-elections/6.png)


