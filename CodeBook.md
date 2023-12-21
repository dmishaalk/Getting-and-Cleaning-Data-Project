---
editor_options: 
  markdown: 
    wrap: 72
---

## Getting and Cleaning Data Project

The data preparation is completed by the run_analysis.R code, which is
then followed by the five stages specified in the project description.

1.  **Downloading data**

Data is downloaded and stored in a folder called 'UCI HAR Dataset'.

2.  **Assigning data-frames**

-   features \<- features.txt : 561 rows, 2 columns. The 3-axial raw
    signals from the accelerometer and gyroscope, designated as tAcc-XYZ
    and tGyro-XYZ, are the source of the features chosen for this
    database.
-   activity \<- activity_labels.txt : 6 rows, 2 columns. A list of the
    tasks completed and their accompanying codes (labels) during the
    measurement sessions.
-   subject_test \<- test/subject_test.txt : 2947 rows, 1 column. It
    includes test results from the volunteer test sudjects that are
    being watched.
-   x_test \<- test/X_test.txt : 2947 rows, 561 columns. It contains the
    recorded features test data.
-   y_test \<- test/y_test.txt : 2947 rows, 1 columns. It contains the
    test results for the code labels for the activities.
-   subject_train \<- test/subject_train.txt : 7352 rows, 1 column. It
    contains the train data of the volunteer subjects being watched.
-   x_train \<- test/X_train.txt : 7352 rows, 561 columns. It contains
    the recorded features train data.
-   y_train \<- test/y_train.txt : 7352 rows, 1 columns. It contains the
    train data for the code labels for the activities.

3.  **Merges the training and the test sets to create one data set**

-   X (10299 rows, 561 columns) is created by merging x_train and x_test
    using rbind() function.
-   Y (10299 rows, 1 column) is created by merging y_train and y_test
    using rbind() function.
-   subject (10299 rows, 1 column) is created by merging subject_train
    and subject_test using rbind() function.
-   merged_data (10299 rows, 563 column) is created by merging subject,
    Y and X using cbind() function.

4.  **Extracts only the measurements on the mean and standard deviation
    for each measurement**

-   tidy_data (10299 rows, 88 columns) is created by subsetting
    merged_data, selecting only columns: subject, code and the
    measurements on the mean and standard deviation (std) for each
    measurement.

5.  **Uses descriptive activity names to name the activities in the data
    set**

-   Complete numbers in the tidy_data code column are substituted with
    the relevant activity from the second column of the activity
    variable.

6.  **Appropriately labels the data set with descriptive variable
    names**

-   code column in tidy_data renamed as activities.
-   Acc in column's name replaced by Accelerometer.
-   Gyro in column's name replaced by Gyroscope.
-   BodyBody in column's name replaced by Body.
-   Mag in column's name replaced by Magnitude.
-   All start with character f in column's name replaced by Frequency.
-   All start with character t in column's name replaced by Time.

7.  **From the data set in step 4, creates a second, independent tidy
    data set with the average of each variable for each activity and
    each subject**

-   Following grouping by subject and activity, tidy_data is summarised
    using the means of each variable for each activity and each subject,
    resulting in final_data (180 rows, 88 columns). Export final_data to
    a file named final_data.txt.
