##Tidy Data CodeBook

###Introduction

In the course project of the coursera "Getting and Cleaning Data" course offered by Johns Hopkins University, a dataset about wearable computing is required to be cleaned and transformed into a tidy dataset. This document serves as the codebook of my tidy dataset.

The original data is collected from experiments carried out with a group of 30 volunteers. Each person performed six activities (WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING) wearing a smartphone (Samsung Galaxy S II) on the waist. Using its embedded accelerometer and gyroscope, 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz are captured. After pre-processing, these sensor signals were then sampled in fixed-width sliding windows of 2.56 sec and 50% overlap (128 readings/window). The sensor acceleration signal was also separated into body acceleration (tBodyAcc) and gravity (tGravityAcc). Subsequently, the body linear acceleration (tBodyAcc) and angular velocity (tBodyGyro) were derived in time to obtain Jerk signals (tBodyAccJerk and tBodyGyroJerk). Also a Fast Fourier Transform (FFT) was applied to some of these time domain signals producing frequency domain signals (fBodyAcc, fBodyAccJerk, fBodyGyro, and fBodyGyroJerk). Finally the magnitude of all these three-dimensional signals were calculated using the Euclidean norm (tBodyAccMag, tGravityAccMag, tBodyAccJerkMag, tBodyGyroMag, tBodyGyroJerkMag, fBodyAccJerkMag, fBodyAccMag, fBodyGyroMag, and fBodyGyroJerkMag).

Within each window, the following measurements were used to estimate variables of the feature vector (including mean and standard deviation) for each pattern ('-XYZ' is used to denote 3-axial signals in the X, Y and Z directions) :

tBodyAcc-XYZ

tGravityAcc-XYZ

tBodyAccJerk-XYZ

tBodyGyro-XYZ

tBodyGyroJerk-XYZ

tBodyAccMag
tGravityAccMag
tBodyAccJerkMag
tBodyGyroMag
tBodyGyroJerkMag
fBodyAcc-XYZ
fBodyAccJerk-XYZ
fBodyGyro-XYZ
fBodyAccMag
fBodyAccJerkMag
fBodyGyroMag
fBodyGyroJerkMag

###My Transformation

Here are the transformations I performed to clean up the data:

*The original data is composed of two components: training data and test data. Either of them is composed of one subject identifier file, one activity file, one feature file, and nine sampled signal data files. I merged the subject identifier file, the activity file, and the feature file in either components, and then combined the training data part and the test data part into one dataset. The nine sampled signal data files are ignored.

*Among the many features, I extracted only the mean and standard deviation for each measurement.

*The original activity files use numbers to represent the activities performed, but I used the corresponding activity names instead to make them more transparent.

*The original feature data does not have variable names, and has its descriptive feature names saved separately in another file. I used those names to label the feature variables as their names. I also named the rest variables in the dataset.

*After all the above transformations, I created a tidy data set with the average of each chosen feature variable for each activity and each subject.

###Data and Variables

The tidy data set contains 180 records and 68 variables, with each record corresponding to each different subject (30 subjects in total) and activity (6 activities in total) combination. The 68 variables are:

*"subject": the identifier of the subject who carried out the experiment. It ranges from 1 to 30.

*"activity": the activity performed. Its value is one of the following six: WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING.

*66 feature variables: they are the average of each chosen feature variable across all windows for each activity and each subject. The chosen features are the means and standard deviations within each window for all the measurements (features in the original data are normalized and bounded within [-1,1]). The naming convention for these 66 feature variables are "'measurement type'-'mean() or std()'-'X or Y or Z'" (the last part "-'X or Y or Z'" is omitted if the measurement is not directional). For example, variable name "tBodyAcc-mean()-X" refers to the average of the mean of the measurement tBodyAcc in the X direction, variable name "tBodyGyroJerk-std()-Z" refers to the average of the standard deviation of measurement tBodyGyroJerk in the Z direction, and variable name "fBodyGyroMag-mean()" refers to the average of the mean of measurement fBodyGyroMag. All the measurement types are listed as the following ('-XYZ' is added to the end of each directional measurement type to denote that it has 3-axial signals in the X, Y and Z directions):

tBodyAcc-XYZ
tGravityAcc-XYZ
tBodyAccJerk-XYZ
tBodyGyro-XYZ
tBodyGyroJerk-XYZ
tBodyAccMag
tGravityAccMag
tBodyAccJerkMag
tBodyGyroMag
tBodyGyroJerkMag
fBodyAcc-XYZ
fBodyAccJerk-XYZ
fBodyGyro-XYZ
fBodyAccMag
fBodyAccJerkMag
fBodyGyroMag
fBodyGyroJerkMag
