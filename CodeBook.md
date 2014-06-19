Code Book
=========


## Raw Data

The raw data are a conjunt of 6 files with data and 2 files with labels

**Data files**

* subject_test.txt
* y_test.txt
* X_test.txt
* subject_train.txt
* Y_train.txt
* X_train.txt

**Explanation:**
* *train and *test are 2 ramdom subsamples for a initial data set.
* subject* are the codes for each subject in the experiment
* Y_* are the codes for each activity
* X_* are the obtained measures

**Labels files**

* features.txt
* activity_labels.txt

**Explanation:**

features.txt containt the names of 561 measures.

activity_labels.txt is the code for each activity:
* 1 WALKING
* 2 WALKING_UPSTAIRS
* 3 WALKING_DOWNSTAIRS
* 4 SITTING
* 5 STANDING
* 6 LAYING


## Processed data

The preparation of data have two main steps:

* Merge all data
* Select relevant data

Once preparation is finished, the new data set have this structure:

No. of observations =  10299 

###  Variable (Class Description)
   
1.  subject (factor). Values: 1 to 30  
2.  practice (factor). Values: WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING
3.  fBodyAcc-mean()-X  (numeric)
4.  fBodyAcc-mean()-Y  (numeric)
5.  fBodyAcc-mean()-Z  (numeric)
6.  fBodyAcc-std()-X  (numeric)
7.  fBodyAcc-std()-Y  (numeric)
8.  fBodyAcc-std()-Z  (numeric)
9.  fBodyAccJerk-mean()-X (numeric)
10. fBodyAccJerk-mean()-Y  (numeric)
11. fBodyAccJerk-mean()-Z  (numeric)
12. fBodyAccJerk-std()-X  (numeric)
13. fBodyAccJerk-std()-Y  (numeric)
14. fBodyAccJerk-std()-Z  (numeric)
15. fBodyGyro-mean()-X  (numeric)
16. fBodyGyro-mean()-Y  (numeric)
17. fBodyGyro-mean()-Z  (numeric)
18. fBodyGyro-std()-X  (numeric)
19. fBodyGyro-std()-Y  (numeric)
20. fBodyGyro-std()-Z  (numeric)
21. fBodyAccMag-mean  (numeric)
22. fBodyAccMag-std()  (numeric)
23. fBodyBodyAccJerkMag-mean()  (numeric)
24. fBodyBodyAccJerkMag-std()  (numeric)
25. fBodyBodyGyroMag-mean()  (numeric)
26. fBodyBodyGyroMag-std (numeric)
27. fBodyBodyGyroJerkMag-mean()  (numeric)
28. fBodyBodyGyroJerkMag-std()  (numeric)

## 2º Processed data

This is a extract of principal data. Is the mean and std for each combination of subject and activity.

Is the same structure, but numeric variables are the mean  of original variables with the same name.
