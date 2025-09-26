# Getting and Cleaning Data - Course Project

## Overview

This repository contains the course project for the "Getting and Cleaning Data" course on Coursera, part of the Data Science Specialization by Johns Hopkins University.

The purpose of the project is to demonstrate the ability to collect, clean, and tidy a data set for analysis.

The data used in this project comes from the [UCI HAR Dataset](http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones), which contains recordings of human activity captured via smartphone accelerometers and gyroscopes.

## Files in This Repository

- `run_analysis.R`: The R script that performs the data cleaning and tidying steps.
- `FinalData.txt`: The final tidy dataset output, containing the average of each variable for each activity and subject.
- `CodeBook.md`: Describes the dataset, variables, and the transformations applied.
- `README.md`: This file, describing the project and how the analysis was done.

## Data Cleaning and Processing Steps

The `run_analysis.R` script performs the following steps:

1. **Merges the training and test datasets** to create one unified data set.
2. **Extracts only the measurements on the mean and standard deviation** for each measurement.
3. **Replaces activity codes with descriptive activity names** for better readability.
4. **Labels the data set with descriptive variable names**, replacing abbreviations with full terms and correcting inconsistent labels.
5. **Creates a second, independent tidy dataset**, containing the average of each variable for each activity and each subject.

## How to Run the Script

To reproduce the analysis, do the following:

1. Download the [UCI HAR Dataset](https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip) and unzip it in your R working directory.
2. Ensure the `run_analysis.R` script is in the same working directory.
3. Run the script in R or RStudio:
   ```R
   source("run_analysis.R")
