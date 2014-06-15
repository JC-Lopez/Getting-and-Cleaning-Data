Readme
======

## 1 IMPORTANT

You need to create and use a working directory "workdir" directly on C: 

` setwd("C:/workdir") `

and unzip the following files there:
* subject_test.txt
* y_test.txt
* X_test.txt
* subject_train.txt
* y_train.txt
* X_train.txt
* features.txt


The "package car" are required

` library(car) ` 


## 2 Load all required data set. 

This operation could take a time. Please, wait.

``` 
subject_test<- read.table("C:/workdir/subject_test.txt", header=FALSE, sep= " ")
y_test<- read.table("C:/workdir/y_test.txt", header=FALSE, sep= " ")
x_test <- read.table("C:/workdir/X_test.txt", header=FALSE, sep="", na.strings="NA", dec=".", strip.white=TRUE)
subject_train<- read.table("C:/workdir/subject_train.txt", header=FALSE, sep= " ")
y_train<- read.table("C:/workdir/y_train.txt", header=FALSE, sep= " ")
x_train <- read.table("C:/workdir/X_train.txt", header=FALSE, sep="", na.strings="NA", dec=".", strip.white=TRUE)
```

## 3 Converted subjects and activities in factors

Your rol is as a factor, no as numeric value.

```
subject_test$V1<- as.factor(subject_test$V1)
subject_train$V1<- as.factor(subject_train$V1)
y_test$V1<- as.factor(y_test$V1)
y_train$V1<- as.factor(y_train$V1)
```

## 4 Create "test" and "train" dataframes

```
test<- data.frame(subject_test, y_test, x_test)
train<- data.frame(subject_train, y_train, x_train)
```

## 5 joint "test" and "train" for create "Total"

` Total<-rbind(test, train) `


## 6 Load table with labels, 

labels for measures are in "features.txt". We call it "labels2"

` labels2<- read.table("C:/workdir/features.txt", header=FALSE, sep="", na.strings="NA", dec=".", strip.white=TRUE) `


## 7 Select col 2 and convert into a vector, with the same name, "labels 2"

` labels2<- as.vector(labels2$V2) `


## 8 Create the final labels, named "labels", 

For this, joint "subjet" y  "practice" with "labels2" vector.

` labels<- c("subject","practice", labels2) `


## 9 Now, we make the names of "labels" to be the names of "Total"

` colnames(Total)<-(labels) `


## 10 Make a new column, the "practice" variable, with activity codes

I use descriptive names for each activity

` Total$practice <- Recode(Total$practice, '1= "Walking"; 2= "Walking_Upstairs"; 3= "Walking_Downstairs"; 4= "Sitting"; 5="Standing"; 6= "Laying"', as.factor.result=TRUE) `


## 11 From dataset "Total", i select only the most important columns 

The criteria is inside the file "features_info.txt": 

Raw data -> Data derived in time -> Fast Fourier transformation

> Finally a Fast Fourier Transform (FFT) was applied to some of these signals producing fBodyAcc-XYZ, fBodyAccJerk-XYZ, fBodyGyro-XYZ, fBodyAccJerkMag, fBodyGyroMag, fBodyGyroJerkMag. (Note the 'f' to indicate frequency domain signals)."

` miscolumnas <- c(1:2, 268:273, 347:352, 426:431, 505:506, 518:519, 531:532, 544:545) ` 

## 12 Subsetting select columns

We use the vector "miscolumnas" to select a "subsetting" dataset from the "total" dataset. The new dataset is "Total2"

` Total2<-Total[,miscolumnas]  ` 


## 13 Write the table. 

Is a txt file, separated whiht 1 space " ".

` write.table(Total2, file = "tabla.txt", sep = " ",
            na = "NA", dec = ".", row.names = FALSE,
            col.names = TRUE) ` 


##  Part 2
## Table with means for subject - activity

`medias<-aggregate(Total2[,3:28], list(Total2$subject, Total2$practice), mean) `

` colnames(medias)<- colnames(Total2) `

```
write.table(medias, file = "means.txt", sep = " ",
                           na = "NA", dec = ".", row.names = FALSE,
                           col.names = TRUE)
```
