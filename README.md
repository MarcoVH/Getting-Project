Getting and Cleaning Data Course Project
=========================

Contents
-----------
This repository contains the following files:
* **run_analysis.R** : Code for calculating a tidy data set as described in the course page.
* **Codebook.md**: File describing the variables of the tidy set generated from run_analysis.
* **README.md**: This file.

¿How the script works?
----------
The objective of the script is to clean and process the data obtained from [here](https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip) to make a tidy data set with a script that does the following in R:

1. Merges the training and the test sets to create one data set.
2. Extracts only the measurements on the mean and standard deviation for each measurement. 
3. Uses descriptive activity names to name the activities in the data set
4. Appropriately labels the data set with descriptive variable names. 
5. From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject.

##Setting up

In order to run the code in run_analysis.R you need to:

1. Download the data from [here](https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip).
2. Unzip to a folder of your choice.
3. Create a copy of run_analysis.R in the same folder.
4. In R, set the working directory to that folder (which contains both, the data folder "UCI HAR Dataset" and the code "run_analysis.R").

##How the code works

1. Checks if you have installed the needed packages and if not it installs it (for this Internet connection is required), then loads the required packages (data.table and reshape2)
2. Loads all the data to the workspace
3. Merges train and test data sets in three parts: 
	1. X: All the measurements
	2. y: The activities ids
	3. subject: The subject ids
4. Extracts/creates the column names for X and subject
5. Adds descriptive labels for y and and names for columns.
6. Discards all measurements of X that are not related to the mean() or std() (_Note: It discards too the variables that are FreqMean and other that are not explicitly "mean()" or "std()" including parenthesis_)
7. Merges X,y and subject to one data frame.
8. Creates tidy data named "Neat" by melt and cast from the reshape2 package with the average of each variable for each activity and each subject.