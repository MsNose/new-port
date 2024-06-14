---
title: "Category KPI donuts in Tableau"
date: 2024-01-13T12:49:27+06:00
featureImage: images/allpost/donut.jpeg
postImage: images/blog/KPI-donuts/title.png
tags: Tableau
categories: blog
---


I have a logistics data set and I wanted to create donut charts in Tableau about the status of the order. There are 3 categories: completed, canceled and pending. The goal of the viz is to show the percentage of this category compared to the total. 

![](/images/blog/KPI-donuts/0.png)


### 1. Create a two-slice pie chart
For this we need the number of orders in a certain order status, and the number of orders belonging to all the other statuses. In this case, I have a total of 500 orders, out of which 27 are cancelled. So, the numbers that I need are 27, and 500-27=473. This seems trivial, however due to Tableau's sensitvity to aggregations, we have to create groups to make this happen.

### 2.  Create category groups
The easiest way is to create groups for each order status, where the dataset is divided into two. In the case of pending, the first group is "PENDING", and the other group is consequently "NOT PENDING", which contains all the remaining orders

![](/images/blog/KPI-donuts/1.png)

In the same manner I created a Completed and Closed group.

### 3. Create a table
Put the newly created order status pending dimension into the rows, and add the count of the Order IDs as text. The correspong order volumes for pending and non-pending orders should be shown.
![](/images/blog/KPI-donuts/2.png)

### 4. Pie chart
Under show me select the pie chart, because after all that is what we are interested in. Notice how the situation off the pills have changed.
![](/images/blog/KPI-donuts/3.png)

### 5. Double axis
Tableau does not have a built in donut chart, so we have to use our creativity and trick the sytem to create an inner circle. Put simply AVG(0) to the rows. It will be automatically aggregated. Add it for the second time, and after right click select dual axis. This way our chart is not going to be depicted twice.

| ![](/images/blog/KPI-donuts/4.png) | ![](/images/blog/KPI-donuts/4.1.png) |
|:------------------------------------:|:------------------------------------:|


### 6. Clear up the chart
Under Format delete the column and row lines, the zero lines and hide the header. Enlarge the pie to  the preferable size

![](/images/blog/KPI-donuts/5.png)
    
### 7. Donut chart 
Now we do the transformation to a donut chart. We simply achieve this by going to the secandary axis, and removing all pills that are there. Change the color to white, and do not panick, the chart did not disappear. The white pieof the secondary axis is just covering the original pie. By reducing the size, we can see the frame of the original pie. 

![](/images/blog/KPI-donuts/6.png)



### 8. Calculated Fields for labels
It is also useful to see the percentage in the middle of the circle. We can do this by putting a label to the the second axis. First, a calculated field  is needed to sum up the pending orders. Second, the percentage is calculated by dividing this number with the total number of orders..

| ![](/images/blog/KPI-donuts/7.1.png) | ![](/images/blog/KPI-donuts/7.2.png) |
|:------------------------------------:|:------------------------------------:|



### 9. Labels
After putting the OrderStatusPending% into percentage format we can drop it to the label of the second axis. I also added the actual number on the label. Edit it according to your taste. You can do that by clicking on the label and selecting the three dots next to "Text".

![](/images/blog/KPI-donuts/8.png)


### 10. Put it all together

Repeat all if these steps for the other two categories (completed, canceled). We can then finally combine all three sheets in a dashboard

![](/images/blog/KPI-donuts/9.png)

What an adventure, but it in 10 steps it is possible to do it!

