Getting and Cleaning Data - Coursera Project

## Project Description
This project aim is to demonstrate my ability to collect, work with, and clean a data set.
The goal is to prepare tidy data that can be used for later analysis.

I will be required to submit:

1. a tidy data set as described below
2. a link to a Github repository with your script for performing the analysis, and
3. a code book that describes the variables, the data, and any transformations or
   work that you performed to clean up the data called CodeBook.md. You should also
   include a README.md in the repo with your scripts. This file explains how all
   of the scripts work and how they are connected. 

Here are the data for the project: https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip

 Code is written in R in file. Source file is run_analysis.R. This R script does the following things:

* Download and unzip the dataset.
* Load activity, subject and feature info. Read data from the files into the variables.
        Read the Activity files.
        Read the Subject files.
        Read Features files.
* Merges the training and the test sets to create one data set.
        Concatenate the data tables by rows.
        set names to variables.
        Merge columns to get the data frame Data for all data.
* Extracts only the measurements on the mean and standard deviation for each measurement. 
        Subset Name of Features by measurements on the mean and standard deviation.
        Subset the data frame Data by selected names of Features.
* Uses descriptive activity names to name the activities in the data set
        Read descriptive activity names from activity_labels.txt
        Sum up variable activity in the data frame Data using descriptive activity names.
* Appropriately labels the data set with descriptive activity names. 
* Creates a independent tidy dataset that consists of the average (mean) value of each variable for each subject and activity.

Final output file is tidydata.txt

## What you find in this repository

* __CodeBook.md__: information about raw and tidy data set and elaboration made to
  transform them
* __README.md__: this file
* __run_analysis.R__: R script to transform raw data set in a tidy one


## How to create the tidy data set

1. clone this repository: `git clone https://github.com/kalyserge/getting-cleaning-data-project.git`
2. download [compressed raw data](https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip)
3. unzip raw data and copy the directory `UCI HAR Dataset` to the cloned repository root directory
4. open a R console and set the working directory to the repository root (use setwd())
5. source run_analisys.R script (it requires the httr package): `source('run_analysis.R')`
