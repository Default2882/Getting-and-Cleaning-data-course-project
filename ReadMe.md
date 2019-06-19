---
title: "ReadME"
output: pdf_document
---
**NOTE : ** Please look at the average-subject-activity.csv to compare it to average-subject-activity.txt

**Getting and Cleaning Data Course Project**

The purpose of this project is to demonstrate your ability to collect, work with, and clean a data set. The goal is to prepare tidy data that can be used for later analysis. You will be graded by your peers on a series of yes/no questions related to the project. You will be required to submit: 1) a tidy data set as described below, 2) a link to a Github repository with your script for performing the analysis, and 3) a code book that describes the variables, the data, and any transformations or work that you performed to clean up the data called CodeBook.md. You should also include a README.md in the repo with your scripts. This repo explains how all of the scripts work and how they are connected.

One of the most exciting areas in all of data science right now is wearable computing - see for example this article . Companies like Fitbit, Nike, and Jawbone Up are racing to develop the most advanced algorithms to attract new users. The data linked to from the course website represent data collected from the accelerometers from the Samsung Galaxy S smartphone. A full description is available at the site where the data was obtained:

http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones

Here are the data for the project:

https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip 

You should create one R script called run_analysis.R that does the following.
1.    Merges the training and the test sets to create one data set.
2.    Extracts only the measurements on the mean and standard deviation for each measurement.
3.    Uses descriptive activity names to name the activities in the data set
4.    Appropriately labels the data set with descriptive variable names.
5    From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject.


**Scripts**
the run_analysis.R scipts can be found in the RCode folder

**Code Documentation**
The main 2 functions are combine() and avg().
The combine function generates a data set which is the combination of the two test and train raw data set in the "Raw data" folder. This data set is saved in the file called findata.csv. As per the instruction of the 4th guideline.
The avg() function creates a tidydata set and stores it in the average-subject-activity.txt file. As per the instruction of the 5th guideline.

(Please read the code alongside of the documentation to get a clear picture of what's going on.)
The testmakedataset and trainmakedataset does the same thing but to their respective datasets.
The function reads the data set and stores it into the variable for example testset, then the features list is read and stored into a variable. Then the features list is searched using regular expression to get the variables which have mean and std in their names, the index is stored in k. Afer searching the list, the names of the mean and std variables are extracted out of the features variable and stored into a 'name' variable. Then the testset is subsetted to get only the columns which contains the mean and standard deviation of the data and the variable names are set using the 'name' variable.
Then all the steps are simple, the Y_test.txt and Subjects columns are read from their respective files and the funtion returns a data frame column binding testset, activity column and the subject column.

The combine() function takes the train data set and the test data set as a dataframe form the respective functions and joins them vertically, hence getting a joint data set of both and saves it into a csv file.

Lastly, the avg() function reads the above file and make a 2 level factor variable out of the subject column and the activity column and saves it into the activity.subject variable.
The next steps combines the activity.subject and the mean variable and **Row Binds them together, which suggests that my tidydata may look diiferent than other because it is row binded**.
(Refer to the average-activity-subject.csv file to see the differences clearly)

