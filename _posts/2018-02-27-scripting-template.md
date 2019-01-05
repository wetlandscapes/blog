---
title: Scripting Template
classes: wide
---

One thing I continually struggle with in R (or any scripting language) is how to organize my code. Over the last 5-ish years I've come up with my own solution for this organization. Below is the current iteration of how I organize script. It is a living document and constantly changing, but it seems to work pretty well for my purposes.

If anyone has examples they'd like to share or suggestions to improve on this work flow, please let me know!


{% highlight r%}
################################################################################
#Project: <Name of the project to which this code applies.>
#Purpose: <Note on why I made this script.>
#File: <Name of this file.>
#By: <Who wrote the script.>
#Start date (DD/MM/YYYY): <Date I started working on this code.>
#R Version: 3.4.3 <The version of R this script was developed in.>
################################################################################

#Libraries---- <All the libraries I'm using for this script>
################################################################################
#library(LakeIsodrology)
#library(GenSA)
#library(tidyverse)
#library(lubridate)


#Working directory---- <Note: I only use this if I'm not using a .Rproj file>
#Ex:
#wd <- "C:/GoogleDrive/UWyo/Dissertation/PanEvaporationStudy"
#setwd(wd)


#Functions---- <Where I either load functions I written elsewhere or where I
# write functions that I will use later in the script>
################################################################################
funcFiles <- list.files(path = "Functions", full.names = TRUE)
for(i in 1:length(funcFiles)){
  source(funcFiles[i], verbose = FALSE)
}


#Load---- <Loading either from source (e.g., xlsx or csv) or outputs from other
# scripts>
################################################################################
#Ex:
#load("Data/R_edit/PanEvaporation.RData")
#load("Data/R_edit/GLEES.RData")


#Organize---- <This is where I do my data manipulations before doing any actual
# data analysis>
################################################################################
#Ex:
#Pan data
# Apply 2 hour averaging filter.
#   Create 2 hour index.
#PanEvaporation$`2hour` <- round_date(PanEvaporation$Date, "2 hours")
#   Apply mean, but only to Fishhook.
#Pan.2h <- PanEvaporation %>%
#  filter(Site == "Fishhook") %>%
#  group_by(`2hour`) %>%
#  summarise(WaterT_Avg = mean(Water_T),
#            WT_Avg = mean(Water_Level))


#Analyze---- <Here is the main part of the script where I do my analysis, 
# whatever that might be.>
################################################################################
#Ex:
# #Evaporation: Ryan and Harleman
# #Define the minimization function - Residual Standard Error (RSE), here.
#RSE <- function(y.obs, y.pred){
#  sqrt(sum((y.obs - y.pred)^2) / (length(y.pred) - 1))
#}
# 
# #Define the objective function.
#obj.func <- function(obs, inputs, params) {
#  y.hat <- E_RyanHarleman(inputs$AirT_Avg, inputs$WaterT_Avg, inputs$WS_Avg,
#                          a = params[1], b = params[2])
#  error <- RSE(obs, y.hat)
#  error
#}
# 
# #Define optimization constraints
#lo <- c(0.00001, 0.00001)
#hi <- c(20, 20)
#global.min <- 0
#tol <- 1e-10
#max.it <- 10
# 
# #Optimize!
#set.seed(34)
#inverse <- GenSA(fn = obj.func, lower = lo, upper = hi,
#                 obs = Daily.ET$Evap, inputs = Daily.ET,
#                 control=list(threshold.stop = global.min + tol,
#                              verbose = TRUE,
#                              maxit = max.it))
# 
#inverse[c("value","par")]
# 
#E.pred <- E_RyanHarleman(Daily.ET$AirT_Avg, Daily.ET$WaterT_Avg,
#                         Daily.ET$WS_Avg,
#                         a = inverse$par[1], b = inverse$par[2])


#Export---- <Here is where I export data. Exports vary from another R file that
# I will use for more detailed analysis (I like to break up complex analysis
# into smaller chunks), xlsx files that I can format for use in Word, or images
# that I use for figures in Word.>
################################################################################


#Bibliography---- <Here is where I consolidate the stack overflow or other non-
# academic resources I might have used. I'll also intersperse both academic and
# non-academic citations and resources throughout the code, as a more explicit
# reminder of where I got stuff from. This just serves as the consolidation
# point for some of that information.
################################################################################


#Explore---- <This section is reserved for doing some initial summaries and data
# visualizations that I use to inspire me for my final data outputs, or
# additional analysis.
################################################################################
{% endhighlight %}
