# Coursera-Getting-Cleaning-Data
Repository for JHU Data Science Getting and Cleaning Data Course

run_analysis.R is an R script which produces a file named tidy_data_set.txt.
The run_analysis.R script must be run with the working directory set to the UCI HAR Dataset.

The run_analysis.R script performs the following actions:

1) Merges the training and the test sets to create one data set.
2) Extracts only the measurements on the mean and standard deviation for each measurement. 
3) Applies descriptive activity names (WALK, LAYING, etc.) to the activities in the data set.
4) Labels the dataset columns with feature names from the original features file. 
5) Creates a second, independent tidy data set with the average of the observations for each feature grouped by activity and subject.

A detailed breakdown of the script is as follows:

Load the plyr and dplyr libraries.

'''python
library(plyr)
library(dplyr)
'''

Load the training and test set files from the working directory:
+ y_train, and y_test are the activities for each observation.
+ subject_train are the subject IDs for each observation.
+ x_train and x_test are the observation data for each feature

'''python
y_train <- read.table("./train/y_train.txt")
x_train <- read.table("./train/X_train.txt")
subject_train <- read.table("./train/subject_train.txt")

y_test <- read.table("./test/y_test.txt")
x_test <- read.table("./test/X_test.txt")
subject_test <- read.table("./test/subject_test.txt")
'''
Merge the x_train and x_test tables into a single data frame using rbind.

'''python
merged_df <- rbind(x_train, x_test)
'''
Read in the features file from the working directory using read.table().
+ Features are the column names for the x_train and x_test files.
'''python
features <- read.table("features.txt", stringsAsFactors = FALSE)
'''
Apply the column names from features to the merged_df dataframe.
'''python
colnames(merged_df) <- features$V2
'''
Remove duplicated columns from merged_df
'''python
merged_df <- merged_df[, !duplicated(colnames(merged_df), fromLast = T)]
'''
Select only columns with 'mean' or 'std' in the name
'''python
merged_df <- select(merged_df, contains("mean", ignore.case = TRUE), contains("std", ignore.case = TRUE))
'''
Read in the activity_labels file.
+ activity_labels are the descriptive names for the activities encoded in the Y-train and y_test files.
+ use the stringsAsFactors = FALSE flag so that strings are not converted into factors
'''python
activity_labels <- read.table("activity_labels.txt", stringsAsFactors = FALSE)
'''
Join Y_train and Y_test into an activities data frame using rbind
'''python
activities <- rbind(y_train, y_test)
'''
Create a labeled_activities_df data frame from the numbered activities data_frame with activity labels corresponding to the activity number ($V1 column).
'''python
labeled_activities <- lapply(activities$V1, function(x) as.character(activity_labels$V2[activity_labels$V1 == x]))
labeled_activities_df <- ldply (labeled_activities, data.frame, stringsAsFactors = FALSE)
'''
Add the activies data frame to the merged data frame as an activites column
'''python
merged_df <- mutate(merged_df, Activity = labeled_activities_df$X..i..)
'''
Join subjects_train and subjects_test into a subjects vector.
'''python
subjects <- rbind(subject_train, subject_test)
'''
Add the subjects data frame to the merged data frame as a subjects column
'''python
merged_df <- mutate(merged_df, Subject = subjects$V1 )
'''
Rearrange columns with Subjects first, then Activities, then all time variables, then freq, then angular
'''python
merged_df <- select(merged_df, Subject, Activity, starts_with('t'), starts_with('f'), starts_with('angle'))
'''
From the merged_df create an independent tidy data set which summarizes the original data set 
with the average of each variable for each activity and each subject
+Use group_by() to create groups based on Subject and Activity
'''python
summary_df <- group_by(merged_df, Subject, Activity)
summary_df <- summarise_each(summary_df, funs(mean))
'''
Write the tidy data set as a txt file created with write.table() using row.name=FALSE 
'''python
write.table(summary_df, file = "tidy_data_set.txt", row.name=FALSE)
'''





