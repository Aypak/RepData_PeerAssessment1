---
title: "Reproducible Research: Peer Assessment 1"
output: 
  html_document:
    keep_md: true
---


## Loading and preprocessing the data

```r
#Libraries to help with data preprocessing and plotting
library(plyr)
library(dplyr)
library(lubridate)
library(ggplot2)

activity <- read.csv("~/R/RepData_PeerAssessment1/activity.csv")

#Change date from factor to POSIXct
activity<- activity %>% mutate(date=ymd(activity$date))
```


## What is mean total number of steps taken per day?

```r
#Data summarized to report sum, mean and median steps per day
steps_per_day<- na.omit(activity) %>% group_by(date) %>% summarize(sum(steps), mean(steps), median(steps))
names(steps_per_day)<-c("date","total_steps","mean","median")
```


```r
with(steps_per_day,plot(date,total_steps,type="h", xlab="Date",ylab="Total Steps", main="Total Steps Per Day"))
```

![plot of chunk histogram_steps_per_day](figure/histogram_steps_per_day-1.png) 

## What is the average daily activity pattern?



## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
