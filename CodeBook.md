Codebook Script run_analysis.R for UCI data set

The experiments have been carried out with a group of 30 volunteers within an age bracket of 19-48 years. Each person performed six activities (walking, walking upstairs, walking downstairs, sitting, standing, laying) wearing a smartphone (Samsung Galaxy S II) on the waist. Using its embedded accelerometer and gyroscope, the researchers (see below) captured 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz. The experiments were video-recorded to label the data manually. The obtained dataset was randomly partitioned into two sets, where 70% of the volunteers was selected for generating the training data and 30% the test data. 

The sensor signals (accelerometer and gyroscope) were pre-processed by applying noise filters and then sampled in fixed-width sliding windows of 2.56 sec and 50% overlap (128 readings/window). The sensor acceleration signal, which has gravitational and body motion components, was separated using a Butterworth low-pass filter into body acceleration and gravity. The gravitational force is assumed to have only low frequency components, therefore a filter with 0.3 Hz cutoff frequency was used. From each window, a vector of features was obtained by calculating variables from the time and frequency domain. 
 
The researchers provided 561 variables.  The script here extracted those variables that contained the mean and standard deviation for frequency and time observations in three dimensions for such items as gravity, acceleration, etc.  The resulting tidy data set contains the subject-activity pairs with the average for a number of variables noted below.
  
[1] "subject"                                  "activity"                                
 [3] "timebodyaccelerationmeanx"                "timebodyaccelerationmeany"               
 [5] "timebodyaccelerationmeanz"                "timegravityaccelerationmeanx"            
 [7] "timegravityaccelerationmeany"             "timegravityaccelerationmeanz"            
 [9] "timebodyaccelerationjerkmeanx"            "timebodyaccelerationjerkmeany"           
[11] "timebodyaccelerationjerkmeanz"            "timebodygyromeanx"                       
[13] "timebodygyromeany"                        "timebodygyromeanz"                       
[15] "timebodygyrojerkmeanx"                    "timebodygyrojerkmeany"                   
[17] "timebodygyrojerkmeanz"                    "timebodyaccelerationmagmean"             
[19] "timegravityaccelerationmagmean"           "timebodyaccelerationjerkmagmean"         
[21] "timebodygyromagmean"                      "timebodygyrojerkmagmean"                 
[23] "frequencybodyaccelerationmeanx"           "frequencybodyaccelerationmeany"          
[25] "frequencybodyaccelerationmeanz"           "frequencybodyaccelerationjerkmeanx"      
[27] "frequencybodyaccelerationjerkmeany"       "frequencybodyaccelerationjerkmeanz"      
[29] "frequencybodygyromeanx"                   "frequencybodygyromeany"                  
[31] "frequencybodygyromeanz"                   "frequencybodyaccelerationmagmean"        
[33] "frequencybodybodyaccelerationjerkmagmean" "frequencybodybodygyromagmean"            
[35] "frequencybodybodygyrojerkmagmean"         "timebodyaccelerationstdx"                
[37] "timebodyaccelerationstdy"                 "timebodyaccelerationstdz"                
[39] "timegravityaccelerationstdx"              "timegravityaccelerationstdy"             
[41] "timegravityaccelerationstdz"              "timebodyaccelerationjerkstdx"            
[43] "timebodyaccelerationjerkstdy"             "timebodyaccelerationjerkstdz"            
[45] "timebodygyrostdx"                         "timebodygyrostdy"                        
[47] "timebodygyrostdz"                         "timebodygyrojerkstdx"                    
[49] "timebodygyrojerkstdy"                     "timebodygyrojerkstdz"                    
[51] "timebodyaccelerationmagstd"               "timegravityaccelerationmagstd"           
[53] "timebodyaccelerationjerkmagstd"           "timebodygyromagstd"                      
[55] "timebodygyrojerkmagstd"                   "frequencybodyaccelerationstdx"           
[57] "frequencybodyaccelerationstdy"            "frequencybodyaccelerationstdz"           
[59] "frequencybodyaccelerationjerkstdx"        "frequencybodyaccelerationjerkstdy"       
[61] "frequencybodyaccelerationjerkstdz"        "frequencybodygyrostdx"                   
[63] "frequencybodygyrostdy"                    "frequencybodygyrostdz"                   
[65] "frequencybodyaccelerationmagstd"          "frequencybodybodyaccelerationjerkmagstd" 
[67] "frequencybodybodygyromagstd"              "frequencybodybodygyrojerkmagstd"     
For each record it is provided:
======================================

- Triaxial acceleration from the accelerometer (total acceleration) and the estimated body acceleration.
- Triaxial Angular velocity from the gyroscope. 
- A 561-feature vector with time and frequency domain variables. 
- Its activity label. 
- An identifier of the subject who carried out the experiment.


===================================================================================================
License:
========
Use of this dataset in publications must be acknowledged by referencing the following publication [1] 

[1] Davide Anguita, Alessandro Ghio, Luca Oneto, Xavier Parra and Jorge L. Reyes-Ortiz. A Public Domain Dataset for Human Activity Recognition Using Smartphones. 21th European Symposium on Artificial Neural Networks, Computational Intelligence and Machine Learning, ESANN 2013. Bruges, Belgium 24-26 April 2013. 

This dataset is distributed AS-IS and no responsibility implied or explicit can be addressed to the authors or their institutions for its use or misuse. Any commercial use is prohibited.

Other Related Publications:
===========================
[2] Davide Anguita, Alessandro Ghio, Luca Oneto, Xavier Parra, Jorge L. Reyes-Ortiz.  Energy Efficient Smartphone-Based Activity Recognition using Fixed-Point Arithmetic. Journal of Universal Computer Science. Special Issue in Ambient Assisted Living: Home Care.   Volume 19, Issue 9. May 2013

[3] Davide Anguita, Alessandro Ghio, Luca Oneto, Xavier Parra and Jorge L. Reyes-Ortiz. Human Activity Recognition on Smartphones using a Multiclass Hardware-Friendly Support Vector Machine. 4th International Workshop of Ambient Assited Living, IWAAL 2012, Vitoria-Gasteiz, Spain, December 3-5, 2012. Proceedings. Lecture Notes in Computer Science 2012, pp 216-223. 

[4] Jorge Luis Reyes-Ortiz, Alessandro Ghio, Xavier Parra-Llanas, Davide Anguita, Joan Cabestany, Andreu Català. Human Activity and Motion Disorder Recognition: Towards Smarter Interactive Cognitive Environments. 21th European Symposium on Artificial Neural Networks, Computational Intelligence and Machine Learning, ESANN 2013. Bruges, Belgium 24-26 April 2013.  

==================================================================================================
Jorge L. Reyes-Ortiz, Alessandro Ghio, Luca Oneto, Davide Anguita and Xavier Parra. November 2013.
