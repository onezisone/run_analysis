##Description:    
It generates a tidy text file based on data collected from the accelerometers from the Samsung Galaxy S smartphone calculating average of all measures by each activity and subjects according to "Getting and cleaning Data" course project requirements.

#### Steps for testing it:
It's not necessary to download Samsung source file and unzip it before executing this code, as it does both steps automatically and manipulate zip file in local work directory.

*Load code:*
```
source("<YourPathHere>run_analysis.R")
```    
*Creates and writes the average dataset (outputfilename parameter is optional. If not specified a Run_analysis_tidy_data.txt named file will be created at local working directory by default):*
```
run_analysis("<outputfilename>")
```
*Verify if file was generated at local working directory:*
```
getpwd()     
```
*Load generated file data in a data set named "d":*
```
d<-read.table("<outputfilename>", header = TRUE)
```
*Check structure:*
```
str(d)                                                  
```
*Check for first 7th rows and first 7th columns of in memory dataset:*
```
d[1:7,1:7]                                               
```
*Check dataset dimensions:*
```
dim(d)                                                   
```
####Parameters:

*outputfilename* : a custom name for the output text file. This parameter is optional. If not specified a Run_analysis_tidy_data.txt named file will be created at the local working directory by default.

####Logic:

It executes the course project requirements, not necessarily in the same order (explained in more detail in Note 2 below). The requirements are:

- Req 1. Merges the training and the test sets to create one data set.
- Req 2. Extracts only the measurements on the mean and standard deviation for each measurement. 
- Req 3. Uses descriptive activity names to name the activities in the data set.
- Req 4. Appropriately labels the data set with descriptive variable names. 
- Req 5. From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject.

######Note 1: 
It is not needed to download zip file as this function does it by itself and stores it in the local working directory.

######Note 2: 
For the sake of simplicity and optimization, not all steps are executed in the above order. Instead, they are executed in the following one:

1. Download file if it does not exists at local working directory.
2. Load common files for both train and test data: features and activiy labels.
3. Load all test related files: x_test, y_test, subject_test.
4. Merge them all in a unique test data table and assign labels and descriptive names to columns (Req 4 and Req 3).
5. Load all train related files: x_train, y_train, subject_train.
6. Merge them all in a unique train data table and assign labels and descriptive names to columns (Req 4 and Req 3).
7. Merge train and test data (Req 1).
8. Extract mean and std measures (Req 2).
9. Calculate average of each variable for each activity and each subject and save it to disk (Req 5).


