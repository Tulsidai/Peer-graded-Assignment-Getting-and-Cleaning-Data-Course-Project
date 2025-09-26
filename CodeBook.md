# CodeBook - Getting and Cleaning Data Course Project

## Overview

This code book summarizes the data, variables, and transformations performed in the course project.

The final data set, `FinalData.txt`, contains the average of each selected variable (mean and standard deviation measurements) for each activity and each subject.

## Source Data

Original dataset: [UCI HAR Dataset](http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones)

Data were collected from the accelerometers and gyroscopes of a Samsung Galaxy S smartphone worn by 30 subjects performing 6 different activities.

## Steps Taken

The `run_analysis.R` script does the following:

1. **Merges training and test data sets** to form one combined data set.
2. **Extracts measurements** related to mean and standard deviation using `grep` on feature names.
3. **Maps activity IDs to descriptive activity names** using `activity_labels.txt`.
4. **Renames variables** to improve clarity by:
   - Expanding abbreviations (e.g., `Acc` to `Accelerometer`)
   - Prefixing time/frequency signals (`t`/`f`) appropriately
   - Removing or replacing symbols like `-` or `()`
5. **Creates a tidy data set** by grouping by subject and activity, and taking the average of each variable.

## Final Variables in `FinalData.txt`

Each row in the final dataset represents a unique **subject-activity pair** (e.g., Subject 1 walking). There are **180 rows** (30 subjects × 6 activities) and **88 variables**.

### Key Variables

- `subject`: Integer (1–30), identifies the subject
- `activity`: Factor, one of the following:
  - `WALKING`
  - `WALKING_UPSTAIRS`
  - `WALKING_DOWNSTAIRS`
  - `SITTING`
  - `STANDING`
  - `LAYING`

### Feature Variables

These are the **average values** of the original mean and standard deviation measurements. All are **numeric**, unitless (normalized). Examples:

- `TimeBodyAccelerometerMeanX`
- `TimeBodyAccelerometerSTDY`
- `TimeGravityAccelerometerMeanZ`
- `FrequencyBodyGyroscopeJerkMeanFreqX`
- `AngleTimeBodyAccelerometerMeanGravity`

> All variable names follow the format:
> **[Domain][Signal][Statistic][Axis]**  
> Where:
> - **Domain** = Time / Frequency
> - **Signal** = BodyAccelerometer, GravityAccelerometer, BodyGyroscope, etc.
> - **Statistic** = Mean or STD
> - **Axis** = X, Y, Z or blank for magnitude-based features

## Transformations

- Used `dplyr::select()` and `contains("mean") | contains("std")` to subset columns.
- Used `dplyr::group_by(subject, activity)` and `summarise_all(mean)` to compute the tidy average data set.

## Output

- File: `FinalData.txt`
- Format: Tab-delimited text
- Rows: 180
- Columns: 88

## Notes

- Only variables containing "mean()" or "std()" were included (meanFreq was excluded unless matched accidentally).
- Variable names were cleaned and made human-readable.
