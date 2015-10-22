---
title: "Tidy Data Codebook"
author: "Brian Joss"
date: "October 22, 2015"
output:
  html_document:
    keep_md: yes

This codebook is based on a template kindly provided by Joris Schut
https://gist.github.com/JorisSchut/dbc1fc0402f28cad9b41
---

## Project Description
This project was created in accordance with the project criteria for the Coursera Getting and Cleaning Data class,
as part of the Johns Hopkins Data Science Specialization. 

The purpose of the project is to create a tidy dataset from the Human Activity Recognition Using Smartphones 
Dataset collected in the following publication:
==================================================================
Human Activity Recognition Using Smartphones Dataset
Version 1.0
==================================================================
Jorge L. Reyes-Ortiz, Davide Anguita, Alessandro Ghio, Luca Oneto.
Smartlab - Non Linear Complex Systems Laboratory
DITEN - Università degli Studi di Genova.
Via Opera Pia 11A, I-16145, Genoa, Italy.
activityrecognition@smartlab.ws
www.smartlab.ws
==================================================================

The data used in this tiday data project were subject, activity, and the mean and standard deviation feature variables published by the 
authors of the original dataset. 
A full description of the original dataset is available at the site where the data was published: 

http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones 


##Study design and data processing
As described by the original researchers the data used in this project were collected and processed as follows:
The experiments have been carried out with a group of 30 volunteers within an age 
bracket of 19-48 years. Each person performed six activities 
(WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING) 
wearing a smartphone (Samsung Galaxy S II) on the waist. 

Using its embedded accelerometer and gyroscope, we captured 3-axial linear acceleration 
and 3-axial angular velocity at a constant rate of 50Hz. The experiments have been 
video-recorded to label the data manually. The obtained dataset has been randomly 
partitioned into two sets, where 70% of the volunteers was selected for generating 
the training data and 30% the test data. 

The sensor signals (accelerometer and gyroscope) were pre-processed by applying 
noise filters and then sampled in fixed-width sliding windows of 2.56 sec and 
50% overlap (128 readings/window). The sensor acceleration signal, which has 
gravitational and body motion components, was separated using a Butterworth 
low-pass filter into body acceleration and gravity. The gravitational force 
is assumed to have only low frequency components, therefore a filter with 
0.3 Hz cutoff frequency was used. From each window, a vector of features was 
obtained by calculating variables from the time and frequency domain. 

See 'features_info.txt' of the original dataset for more details. 

##Creating the tidy datafile
The tidy data file presented in this project was created from the original dataset as follows:
1) The training and the test set feaure, activity, and subject data files (X_train, X_test, y_train, y_test, subject_train and subject_test data files) were merged to create one data set. 
2) The feature data from the X_train and X_test files were filtered to retain only feature data representing either a mean or standard deviation feature observation.
3) The activity data from the y_train and y_test data represented as integers from 1 to 6 were replaced by text strings representing the activities according to the
 associations presented in the activitiy_labels file in the original dataset as follows:

1 WALKING
2 WALKING_UPSTAIRS
3 WALKING_DOWNSTAIRS
4 SITTING
5 STANDING
6 LAYING
 
4) The data set was labled with descriptive variable names as follows:
The subject data were labled as "Subject", the activities as "Activity", and the retained feature variables were named in accordance with the corresponding name from the features file in the original data set.
5) From the dataset in step 4, a second, independent tidy data set with the average of each feature variable for each activity and each subject was created and stored in a file named  tidy_data_set.txt


###Guide to create the tidy data file
To recreate the tidy_data_set.txt file, perform the following steps:

1) Download a zip file containing the original Human Activity Recognition Using Smartphones Dataset from 

https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip 

2) Unzip the datafile.
3) Using the UCI HAR Dataset as your working directory, run the run_analysis.R script. This will produce the file tidy_data_set.txt in the working directory.

###Cleaning of the data
The original data were cleaned by 

The cleaning script run_analysis.R is described in greater detail in the README.md file located at:
https://github.com/ThorDog/Coursera-Getting-Cleaning-Data

Short, high-level description of what the cleaning script does. [link to the readme document that describes the code in greater detail]()

##Description of the variables in the tiny_data.txt file
General description of the file including:
 - Dimensions of the dataset:
	The tidy dataset consists of 180 observations of 88 variables.
 - Summary of the data
	The data consists of observations for 30 subjects for each of 6 activites 
(WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING)
The observations are the average of each of the feature variables selected for inclusion in this dataset.
 
 - Variables present in the dataset

(you can easily use Rcode for this, just load the dataset and provide the information directly form the tidy data file)

###Variable 1 (repeat this section for all variables in the dataset)
Short description of what the variable describes.

Some information on the variable including:
 - Class of the variable
 - Unique values/levels of the variable
 - Unit of measurement (if no unit of measurement list this as well)
 - In case names follow some schema, describe how entries were constructed (for example time-body-gyroscope-z has 4 levels of descriptors. Describe these 4 levels). 

(you can easily use Rcode for this, just load the dataset and provide the information directly form the tidy data file)

####Notes on variable 1:
If available, some additional notes on the variable not covered elsewehere. If no notes are present leave this section out.

### Variable 1: 'Subject'
integer values 1 to 30 identifying each of the subjects in the dataset.
No units of measure for this variable.

### Variable 2: 'Activity'
character data consisting of one of 6 activities.
WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING

No units of measure for this variable.

### Variables 3, 4, 5:  tBodyAcc-mean()-X, -Y, -Z
data type is numerical in the range of -1 to 1.

Data represent the average values of the mean time value of the body accelerometer in the X, Y, and Z axis
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for these variables.

### Variables 6, 7, 8:  tGravityAcc-mean()-X, -Y, -Z
data type is numerical in the range of -1 to 1.

Data represent the average values of the mean time value of the gravitational acceleration in the X, Y, and Z axis
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for these variables.

### Variables 9, 10, 11:  tBodyAccJerk-mean()-X, -Y, -Z
data type is numerical in the range of -1 to 1.

Data represent the average values of the mean time value of the body accelerometer jerk in the X, Y, and Z axis
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for these variables.

### Variables 12, 13, 14:  tBodyGyro-mean()-X, -Y, -Z
data type is numerical in the range of -1 to 1.

Data represent the average values of the mean time value of the body gyro in the X, Y, and Z axis
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for these variables.

### Variables 15, 16, 17:  tBodyGyroJerk-mean()-X, -Y, -Z
data type is numerical in the range of -1 to 1.

Data represent the average values of the mean time value of the body gyro jerk in the X, Y, and Z axis
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for these variables.

### Variable 18:  tBodyAccMag-mean()
data type is numerical in the range of -1 to 1.

Data represent the average values of the mean time value of the body accelerometer magnitude
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for this variable.

### Variable 19:  tGravityAccMag-mean()
data type is numerical in the range of -1 to 1.

Data represent the average values of the mean time value of the gravity accelerometer magnitude
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for this variable.

### Variable 20:  tBodyAccJerkMag-mean()
data type is numerical in the range of -1 to 1.
 
Data represent the average values of the mean time value of the body accelerometer jerk magnitude
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for this variable.

### Variable 21:  tBodyGyroMag-mean()
data type is numerical in the range of -1 to 1.

Data represent the average values of the mean time value of the body gyro magnitude
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for this variable.

### Variable 22:  tBodyGyroJerkMag-mean()
data type is numerical in the range of -1 to 1.

Data represent the average values of the mean time value of the body gyro jerk magnitude
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for this variable.

### Variables 23, 24, 25:  tBodyAcc-std()-X, -Y, -Z
data type is numerical in the range of -1 to 1.

Data represent the average values of the standard deviation of the time value of the body accelerometer in the X, Y, and Z axis
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for these variables.

### Variables 26, 27, 28:  tGravityAcc-std()-X, -Y, -Z
data type is numerical in the range of -1 to 1.

Data represent the average values of the standard deviation of the time value of the gravitational accelerometer in the X, Y, and Z axis
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for these variables.

### Variables 29, 30, 31:  tBodyAccJerk-std()-X, -Y, -Z
data type is numerical in the range of -1 to 1.

Data represent the average values of the standard deviation of the time value of the body accelerometer jerk in the X, Y, and Z axis
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for these variables.

### Variables 32, 33, 34:  tBodyGyro-std()-X, -Y, -Z
data type is numerical in the range of -1 to 1.

Data represent the average values of the standard deviation of the time value of the body gyro in the X, Y, and Z axis
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for these variables.

### Variables 35, 36, 37:  tBodyGyroJerk-std()-X, -Y, -Z
data type is numerical in the range of -1 to 1.

Data represent the average values of the standard deviation of the time value of the body gyro jerk in the X, Y, and Z axis
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for these variables.


### Variable 38:  tBodyAccMag-std()
data type is numerical in the range of -1 to 1.

Data represent the average values of the standard deviation of the time value of the body accelerometer magnitude
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for this variable.

### Variable 39:  tGravityAccMag-mean()
data type is numerical in the range of -1 to 1.

Data represent the average values of the standard deviation of the time value of the gravity accelerometer magnitude
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for this variable.

### Variable 40:  tBodyAccJerkMag-std()
data type is numerical in the range of -1 to 1.

Data represent the average values of the standard deviation of the time value of the body accelerometer jerk magnitude
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for this variable.

### Variable 41:  tBodyGyroMag-std()
data type is numerical in the range of -1 to 1.

Data represent the average values of the standard deviation of the time value of the body gyro magnitude
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for this variable.

### Variable 42:  tBodyGyroJerkMag-std()
data type is numerical in the range of -1 to 1.

Data represent the average values of the standard deviation of the time value of the body gyro jerk magnitude
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for this variable.

### Variables 43, 44, 45:  fBodyAcc-mean()-X, -Y, -Z
data type is numerical in the range of -1 to 1.

Data represent the average values of the mean of the frequency domain value of the body accelerometer in the X, Y, and Z axis
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for these variables.

### Variables 46, 47, 48:  fBodyAcc-meanFreq()-X, -Y, -Z
data type is numerical in the range of -1 to 1.

Data represent the average values of the mean of the frequency domain value of the body accelerometer frequencies in the X, Y, and Z axis
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for these variables.

### Variables 49, 50, 51:  fBodyAccJerk-mean()-X, -Y, -Z
data type is numerical in the range of -1 to 1.

Data represent the average values of the mean of the frequency domain value of the body accelerometer jerk in the X, Y, and Z axis
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for these variables.

### Variables 52, 53, 54:  fBodyAccJerk-meanFreq()-X, -Y, -Z
data type is numerical in the range of -1 to 1.

Data represent the average values of the mean of the frequency domain value of the body accelerometer jerk frequencies in the X, Y, and Z axis
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for these variables.

### Variables 55, 56, 57:  fBodyGyro-mean()-X, -Y, -Z
data type is numerical in the range of -1 to 1.

Data represent the average values of the mean of the frequency domain value of the body gyro in the X, Y, and Z axis
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for these variables.

### Variables 58, 59, 60:  fBodyGyro-meanFreq()-X, -Y, -Z
data type is numerical in the range of -1 to 1.

Data represent the average values of the mean of the frequency domain value of the body gyro frequencies in the X, Y, and Z axis
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for these variables.

### Variables 61:  fBodyAccMag-mean()
data type is numerical in the range of -1 to 1.

Data represent the average values of the mean of the frequency domain value of the body accelerometer magnitude
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for this variable.

### Variables 62:  fBodyAccMag-meanFreq()
data type is numerical in the range of -1 to 1.

Data represent the average values of the mean of the frequency domain value of the body accelerometer magnitude frequencies
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for this variable.

### Variables 63:  fBodyBodyAccJerkMag-mean()
data type is numerical in the range of -1 to 1.

Data represent the average values of the mean of the frequency domain value of the body accelerometer jerk magnitude
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for this variable.

### Variables 64:  fBodyBodyAccJerkMag-meanFreq()
data type is numerical in the range of -1 to 1.

Data represent the average values of the mean of the frequency domain value of the body accelerometer jerk magnitude frequencies
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for this variable.

### Variables 65:  fBodyBodyGyroMag-mean()
data type is numerical in the range of -1 to 1.

Data represent the average values of the mean of the frequency domain value of the body gyro magnitude
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for this variable.

### Variables 66:  fBodyBodyGyroMag-meanFreq()
data type is numerical in the range of -1 to 1.

Data represent the average values of the mean of the frequency domain value of the body gyro magnitude frequencies
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for this variable.

### Variables 65:  fBodyBodyGyroJerkMag-mean()
data type is numerical in the range of -1 to 1.

Data represent the average values of the mean of the frequency domain value of the body gyro jerk magnitude
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for this variable.

### Variables 66:  fBodyBodyGyroJerkMag-meanFreq()
data type is numerical in the range of -1 to 1.

Data represent the average values of the mean of the frequency domain value of the body gyro magnitude jerk frequencies
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for this variable.

### Variables 67, 68, 69:  fBodyAcc-std()-X, -Y, -Z
data type is numerical in the range of -1 to 1.

Data represent the average values of the standard deviation of the frequency domain value of the body accelerometer in the X, Y, and Z axis
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for these variables.

### Variables 70, 71, 72:  fBodyAccJerk-std()-X, -Y, -Z
data type is numerical in the range of -1 to 1.

Data represent the average values of the standard deviation of the frequency domain value of the body accelerometer jerk in the X, Y, and Z axis
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for these variables.

### Variables 73, 74, 75:  fBodyGyro-std()-X, -Y, -Z
data type is numerical in the range of -1 to 1.

Data represent the average values of the standard deviation of the frequency domain value of the body gyro in the X, Y, and Z axis
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for these variables.

### Variable 76:  fBodyAccMag-std()
data type is numerical in the range of -1 to 1.

Data represent the average values of the standard deviation of the frequency domain value of the body accelerometer magnitude
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for this variable.

### Variable 77:  fBodyBodyAccJerkMag-std()
data type is numerical in the range of -1 to 1.

Data represent the average values of the standard deviation of the frequency domain value of the body accelerometer jerk magnitude
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for this variable.

### Variable 78:  fBodyBodyGyroMag-std()
data type is numerical in the range of -1 to 1.

Data represent the average values of the standard deviation of the frequency domain value of the body gyro magnitude
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for this variable.

### Variables 79:  fBodyBodyGyroJerkMag-std()
data type is numerical in the range of -1 to 1.

Data represent the average values of the standard deviation of the frequency domain value of the body gyro jerk magnitude
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for this variable.

### Variable 80:  angle(tBodyAccMean,gravity)
data type is numerical in the range of -1 to 1.

Data represent the average values of the angle between the body accelerometermean direction vector and the gravity vector
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for this variable.

### Variable 81:  angle(tBodyAccJerkMean),gravityMean)
data type is numerical in the range of -1 to 1.

Data represent the average values of the angle between the body accelerometerjerk mean direction vector and the gravity vector
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for this variable.

### Variable 82:  angle(tBodyGyroMean,gravityMean)
data type is numerical in the range of -1 to 1.

Data represent the average values of the angle between the body gyro mean direction vector and the gravity vector
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for this variable.

### Variable 83:  angle(tBodyGyroJerkMean,gravityMean)
data type is numerical in the range of -1 to 1.

Data represent the average values of the angle between the body gyro jerk mean direction vector and the gravity vector
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for this variable.

### Variable 84:  angle(X,gravityMean)
data type is numerical in the range of -1 to 1.

Data represent the average values of the angle between the X axis and the gravity vector
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for this variable.

### Variable 85:  angle(X,gravityMean)
data type is numerical in the range of -1 to 1.

Data represent the average values of the angle between the X axis and the gravity vector
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for this variable.

### Variable 86:  angle(X,gravityMean)
data type is numerical in the range of -1 to 1.

Data represent the average values of the angle between the X axis and the gravity vector
normalized to the range of -1 to 1.
Because the data are normalized, there are no units of measure for this variable.


##Sources
Use of the Human Activity Recognition Using Smartphones Dataset in publications must be acknowledged by referencing the following publication [1] 

[1] Davide Anguita, Alessandro Ghio, Luca Oneto, Xavier Parra and Jorge L. Reyes-Ortiz. Human Activity Recognition on Smartphones using a Multiclass Hardware-Friendly Support Vector Machine. International Workshop of Ambient Assisted Living (IWAAL 2012). Vitoria-Gasteiz, Spain. Dec 2012

This dataset is distributed AS-IS and no responsibility implied or explicit can be addressed to the authors or their institutions for its use or misuse. Any commercial use is prohibited.

Jorge L. Reyes-Ortiz, Alessandro Ghio, Luca Oneto, Davide Anguita. November 2012.



