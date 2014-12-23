Practical-Machine-Learning-WALTER
=================================

Repo for a Coursera Assignment

PRACTICAL MACHINE LEARNING – Project Writeup
Student:  James Walter

NB: I am new to R and so could not master the R Markdown tool in time to submit this assignment.  Hence, all my methodology and results are here.

To complete this assignment I completed the following steps:
Data Exploration
•	I used excel, which I am the most familiar, to explore structure and nature of the data
•	I noticed many columns that were not measurements of the physical exercise, and so I cut these out prior to entering the training data into R
Model Building
•	After importing the training set of data into R I converted the classe column to a factor
•	In selecting a model method, I reasoned that a classification type of method was the most appropriate since we are predicting a discrete number of values (five classes)
•	I selected Random Forest as my method since I had the time and computing power – I reasoned this algorithm would flush out all the information residing in the training set.
•	The command line was 
modelfit <- train(pml$classe ~., data=pml, method = "rf", preProc = c("center", "scale"))
Results
> modelfit
Random Forest 

19216 samples
   52 predictor
    5 classes: 'A', 'B', 'C', 'D', 'E' 

Pre-processing: centered, scaled 
Resampling: Bootstrapped (25 reps) 

Summary of sample sizes: 19216, 19216, 19216, 19216, 19216, 19216, ... 

Resampling results across tuning parameters:

  mtry  Accuracy   Kappa      Accuracy SD  Kappa SD   
   2    0.9926677  0.9907236  0.001061022  0.001340457
  27    0.9923104  0.9902714  0.001297441  0.001640343
  52    0.9844129  0.9802790  0.003766793  0.004764727

Accuracy was used to select the optimal model using  the largest value.
The final value used for the model was mtry = 2. 


Prediction for Test Data
The Random Forest model was then applied to the Test data, with the following prediction made:
> predict(modelfit, pml.testing)
 [1] B A B A A E D B A A B C B A E E A B B B
Levels: A B C D E


