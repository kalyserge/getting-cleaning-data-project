#### Code Book
Getting and Cleaning Data - Coursera Project
========


### Description


Additional information about the variables, data and transformations used in the course project for the Johns Hopkins Getting and Cleaning Data course.



### Source Data


A full description of the data used in this project can be found at [The UCI Machine Learning Repository](http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones)

[The source data for this project can be found here.](https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip)



### Data Set Information

The experiments have been carried out with a group of 30 volunteers within an age bracket of 19-48 years. Each person performed six activities (WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING) wearing a smartphone (Samsung Galaxy S II) on the waist. Using its embedded accelerometer and gyroscope, we captured 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz. The experiments have been video-recorded to label the data manually. The obtained dataset has been randomly partitioned into two sets, where 70% of the volunteers was selected for generating the training data and 30% the test data. 


The sensor signals (accelerometer and gyroscope) were pre-processed by applying noise filters and then sampled in fixed-width sliding windows of 2.56 sec and 50% overlap (128 readings/window). The sensor acceleration signal, which has gravitational and body motion components, was separated using a Butterworth low-pass filter into body acceleration and gravity.
The gravitational force is assumed to have only low frequency components, therefore a filter with 0.3 Hz cutoff frequency was used. From each window, a vector of features was obtained by calculating variables from the time and frequency domain.


The set of variables that were estimated from these signals are: 

*  mean(): Mean value
*  std(): Standard deviation
*  mad(): Median absolute deviation 
*  max(): Largest value in array
*  min(): Smallest value in array
*  sma(): Signal magnitude area
*  energy(): Energy measure. Sum of the squares divided by the number of values. 
*  iqr(): Interquartile range 
*  entropy(): Signal entropy
*  arCoeff(): Autoregression coefficients with Burg order equal to 4
*  correlation(): Correlation coefficient between two signals
*  maxInds(): Index of the frequency component with largest magnitude
*  meanFreq(): Weighted average of the frequency components to obtain a mean frequency
*  skewness(): Skewness of the frequency domain signal 
*  kurtosis(): Kurtosis of the frequency domain signal 
*  bandsEnergy(): Energy of a frequency interval within the 64 bins of the FFT
   of each window.
*  angle(): Angle between some vectors.

No unit of measures is reported as all features were normalized and bounded
within [-1,1].

### Data transformation
-------------------

The raw data sets are processed with run_analisys.R script to create a tidy data
set [[12](#tidy-dataset)].

## Merge training and test sets

Test (subject_test.txt, X_test.txt, y_test.txt) and training (subject_train.txt, X_train.txt, y_train.txt) data are merged to obtain
a single data set. Variables are labelled with the names assigned by original
collectors (features.txt).

### Extract mean and standard deviation variables

From the merged data set is extracted and intermediate data set with only the
values of estimated mean (variables with labels that contain "mean") and standard
deviation (variables with labels that contain "std").

### Use descriptive activity names

A new column is added to intermediate data set with the activity description.
Activity id column is used to look up descriptions in activity_labels.txt.

### Label variables appropriately

Labels given from the original collectors were changed:
* to obtain valid R names without parentheses, dashes and commas
* to obtain more descriptive labels

### Create a tidy data set

From the intermediate data set is created a final tidy data set where numeric
variables are averaged for each activity and each subject.

The tidy data set contains 10299 observations with 81 variables divided in:

*  an activity label (__Activity__): WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING
*  an identifier of the subject who carried out the experiment (__Subject__):
   1, 3, 5, 6, 7, 8, 11, 14, 15, 16, 17, 19, 21, 22, 23, 25, 26, 27, 28, 29, 30
*  a 79-feature vector with time and frequency domain signal variables (numeric)

The following table relates the 17 signals to the names used as prefix for the
variables names present in the data set. ".XYZ" denotes three variables, one for each axis.

Name                                  | Time domain                                 | Frequency domain
------------------------------------- | ------------------------------------------- | ------------------------------------------------
Body Acceleration                     | TimeDomain.BodyAcceleration.XYZ             | FrequencyDomain.BodyAcceleration.XYZ
Gravity Acceleration                  | TimeDomain.GravityAcceleration.XYZ          |
Body Acceleration Jerk                | TimeDomain.BodyAccelerationJerk.XYZ         | FrequencyDomain.BodyAccelerationJerk.XYZ
Body Angular Speed                    | TimeDomain.BodyAngularSpeed.XYZ             | FrequencyDomain.BodyAngularSpeed.XYZ
Body Angular Acceleration             | TimeDomain.BodyAngularAcceleration.XYZ      |
Body Acceleration Magnitude           | TimeDomain.BodyAccelerationMagnitude        | FrequencyDomain.BodyAccelerationMagnitude
Gravity Acceleration Magnitude        | TimeDomain.GravityAccelerationMagnitude     |
Body Acceleration Jerk Magnitude      | TimeDomain.BodyAccelerationJerkMagnitude    | FrequencyDomain.BodyAccelerationJerkMagnitude
Body Angular Speed Magnitude          | TimeDomain.BodyAngularSpeedMagnitude        | FrequencyDomain.BodyAngularSpeedMagnitude
Body Angular Acceleration Magnitude   | TimeDomain.BodyAngularAccelerationMagnitude | FrequencyDomain.BodyAngularAccelerationMagnitude

For variables derived from mean and standard deviation estimation, the previous labels
are augmented with the terms "Mean" or "StandardDeviation".

The data set is written to the file sensor_avg_by_act_sub.txt.

References
----------

1.  <a name="uci-har"/>Human Activity Recognition Using Smartphones Data Set.
    URL: <http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones>. Accessed 05/21/2014
2. <a name="har-smart"/>Davide Anguita, Alessandro Ghio, Luca Oneto, Xavier Parra and Jorge L. Reyes-Ortiz.
   *Human Activity Recognition on Smartphones using a Multiclass Hardware-Friendly Support Vector Machine*.
   International Workshop of Ambient Assisted Living (IWAAL 2012). Vitoria-Gasteiz, Spain. Dec 2012
3.  <a name="activity-recognition"/>Activity recognition. URL: <http://en.wikipedia.org/wiki/Activity_recognition>.
    Accessed 05/21/2014
4. <a name="har-smart2"/>Davide Anguita, Alessandro Ghio, Luca Oneto, Xavier Parra and Jorge L. Reyes-Ortiz.
   *A Public Domain Dataset for Human Activity Recognition Using Smartphones*.
   ESANN 2013 proceedings, European Symposium on Artificial Neural Networks, Computational Intelligence and
   Machine Learning. Bruges (Belgium), 24-26 April 2013
5.  <a name="time-domain"/>Time domain. URL: <http://en.wikipedia.org/wiki/Time-domain>.
    Accessed 05/21/2014
6.  <a name="hertz"/>Hertz. URL: <http://en.wikipedia.org/wiki/Hertz>. Accessed 05/21/2014
7.  <a name="jerk"/>Jerk. URL: <http://en.wikipedia.org/wiki/Jerk_(physics)>. Accessed 05/21/2014
8.  <a name="magnitude"/>Magnitude. URL: <http://en.wikipedia.org/wiki/Magnitude_(mathematics)>. Accessed 05/21/2014
9.  <a name="euclidean-norm"/>Euclidean norm. URL: <http://en.wikipedia.org/wiki/Norm_(mathematics)#Euclidean_norm>.
    Accessed 05/21/2014
10.  <a name="fft"/>Fast Fourier transform. URL: <http://en.wikipedia.org/wiki/Fast_Fourier_Transform>.
     Accessed 05/21/2014
11.  <a name="freq-domain"/>Frequency domain. URL: <http://en.wikipedia.org/wiki/Frequency_domain>.
     Accessed 05/21/2014
12.  <a name="tidy-dataset"/>Tidy data set. URL: <https://github.com/jtleek/datasharing#the-tidy-data-set>.
     Accessed 05/21/2014
13. <a name="Heather Glenn Wade"/>Heather Glenn Wade. URL: <https://github.com/hglennrock/getting-cleaning-data-project/blob/master/CodeBook.MD>.
14. <a name="Pradeep K. Pant"/>Pradeep K. Pant. URL: <https://github.com/ppant/getting-and-cleaning-data-project-coursera/blob/master/codebook.md>.
15. <a name="Abu Nayeem"/>Abu Nayeem. URL: <https://rstudio-pubs-static.s3.amazonaws.com/30578_9519a6fce3524cc5a21dfba8c9ef6e69.html>.
16. <a name="Mauro Taraborelli"/>Mauro Taraborelli. URL: <https://bitbucket.org/maurotrb/getting-cleaning-data-2014-project/src>.
