# CleanData
repository for coursework with Getting and Cleaning Data Course Project
The runanalysis.R script (listed below) creates one tidy dataset from a number of files.  The raw data is inertia signals  from Smartphones worn by 30 volunteers during various activities, e.g. walking, resting. Researchers summarized the raw data in a data set that provided 561 variables.    The files provided listed the volunteers by number which was combined with the activity file and variables for both test and training datasets.  The runanalysis script extracts mean and standard deviation calculations from the data set.  

The runanalysis script uses the functions in two packages, dplyr and reshape2.  The script reads data from 8 files.  Two files, features.txt and activity_labels.txt, are character labels for the 561 variables and the six different activities.  The subjects are numbered 1-30 that the researchers randomly assigned to two groups, test and train.  Of the 561, only 66 contain the mean or standard deviation.  The script extracts  these 66 columns.   The script creates one large data file with the subject number, the activity labels, the 66 variables.  Many observations are in the data for each subject-activity.  These are filtered from the data set and averaged (mean).



 
library(dplyr)
xtest <- read.table("test/X_test.txt",sep = "")  ## read in obervations for the test group
features <- read.table("features.txt", sep = "")  ## read in variable names
features[,2] <- gsub("\\()","",features[,2])  ## remove parens to minimize confusion
features[,2] <- gsub("meanFreq","MEANfreq",features[,2])  ## remove meanfrequency from subsetting below on mean
activitylabels <- read.table("activity_labels.txt", sep = "")  ##read in names of activity
activitylabels[,2] <- tolower(activitylabels[,2]) ## lower case labels
tt <- grep("mean",features$V2, fixed = TRUE) ## finds variables with mean in name
tu <- grep("std",features$V2)  ## finds variable with std in names
meantest <- select(xtest, tt)  ## subset columns corresponding to variables with mean
stdtest <- select(xtest, tu)  ## subset columns corresponding to variables with std
ytest <- read.table("test/Y_test.txt",sep = "") ## read activity pointers to labels for test group
subtest <- read.table("test/subject_test.txt",sep = "") ##read subject points for test group
subtrain <- read.table("train/subject_train.txt",sep = "")  ##read subject points for train group
ytrain <- read.table("train/Y_train.txt",sep = "")  ## read activity pointers to labels for train group  
xtrain <- read.table("train/X_train.txt",sep = "")  ## read in obervations for the train group
meantrain <- select(xtrain, tt)  ## susbset the train observations for those variables corresponding to variables with means
stdtrain <- select(xtrain, tu)  ## susbset the train observations for those variables corresponding to variables with std
subtest <- data.frame(subtest)  ## build test data frame subjects
test <- cbind(subtest,ytest)  ## add activity to test data
test <- cbind(test,meantest)  ## add variables with mean to test data
test <- cbind(test,stdtest)  ## add variables with std to test data
subtrain <- data.frame(subtrain)  ## build train data frame
train <- cbind(subtrain,ytrain)  ## add activity to train data
train <- cbind(train,meantrain)  ## add variables with mean to train data
train <- cbind(train,stdtrain)  ##  add variables with std to test data
total <- rbind(test,train) ## merge dataframe test and train 
## replace column names with understandable varible names 
names(total)[1:2] <- c("subject","activity")  ## first columns replaced
for(i in seq_along(tt)) {names(total)[i+2] <- as.character(features[tt[i],2])}  ## add column names for means from features
for(i in seq_along(tu)) {names(total)[i+35] <- as.character(features[tu[i],2])}  ## add column names for means from features
## substitute more readable names, time for t, frequency for f, all lower case
names(total) <- sub("fBody","frequencybody",names(total))  ## tidy up variable names, frequency for f
names(total) <- sub("tBody","timebody",names(total))  ## tidy up variable names, time for t
names(total) <- sub("tGravity","timegravity",names(total))  ## tidy up variable names, time for t
names(total) <- sub("Acc","acceleration",names(total)) ## tidy up variable names, acceleration for Acc
names(total)  <- tolower(names(total))  ## tidy up variable names, make variable names lower case
total$activity <- activitylabels[total$activity,2]  ## replace descriptive labels for activity pointers
names(total) <- gsub("-","",names(total))  ## tidy up variable names, remove -
library(reshape2)
## melt data frame, to facilitate one observation for each subject-activity pair
newtot <- melt(total, id.vars = c("subject","activity"))  
tidysmartphone <- dcast(newtot, subject + activity ~ variable, fun.aggregate = mean)
